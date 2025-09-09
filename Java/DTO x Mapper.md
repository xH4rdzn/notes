___
- **DTO** -> é uma abstração, quando se trata da *arquitetura de camadas*, os **DTO's** são um clone da nossa entidade.
- **DTO** -> *Data Transfer Object*
- Vamos precisar de **DTO's** toda vez que quisermos tirar a responsabilidade do nosso *Model*, de conversar com as outras camadas.
- Para criar um **DTO**, seguimos o exemplo:
```java
// NinjaDTO.java

@Data
@AllArgsConstructor
@NoArgsConstructor
public class NinjaDTO {
	
	private long id;
	private String name;
	private String email;
	private String imgUrl;
	private int idade;
	private String rank;
	private MissoesModel missoes;
}
```
- Agora que temos uma cópia(**DTO**), podemos editar o nosso *Model*, para adicionar 'colunas' que foram adicionadas via **migrations**;
- Para podermos utilizar o *DTO*, precisamos fazer o mapeamento, o que chamamos de **Mapper**;
- E para fazer esse *Mapper*, seguimos como no exemplo abaixo:
```java
// NinjaMapper.java

@Component
public class NinjaMapper {
	
	public NinjaModel map(NinjaDTO ninjaDTO) {
		NinjaModel ninjaModel = new NinjaModel();
		ninjaModel.setId(NinjaDTO.getId());
		ninjaModel.setName(NinjaDTO.getName());
		ninjaModel.setEmail(NinjaDTO.getEmail());
		ninjaModel.setIdade(NinjaDTO.getIdade());
	ninjaModel.setImgUrl(NinjaDTO.getImgUrl());
		ninjaModel.setRank(NinjaDTO.getRank());
	ninjaModel.setMissoes(NinjaDTO.getMissoes);
	
		return ninjaModel;
	}
	
	public NinjaDTO map(NinjaModel ninjaModel) {
		NinjaDTO ninjaDTO = new NinjaDTO();
		ninjaDTO.setId(ninjaModel.getId());
		ninjaDTO.setName(ninjaModel.getName());
		ninjaDTO.setEmail(ninjaModel.getEmail());
		ninjaDTO.setImgUrl(ninjaModel.getImgUrl());
		ninjaDTO.setIdade(ninjaModel.getIdade());
		ninjaDTO.setMissoes(ninjaModel.getMissoes());
		ninjaDTO.setRank(NinjaModel.getRank());
		
		return ninjaDTO;
	}
	
}
```
- E agora para poder usar fazemos como no exemplo:
```java
// Inicializamos uma instancia do nosso mapper

private NinjaRepository ninjaRepository;
private NinjaMapper ninjaMapper;

public NinjaService(NinjaRepository ninjaRepository, NinjaMapper ninjaMapper) {
	this.ninjaRepository = ninjaRepository;
	this.ninjaMapper = ninjaMapper;
}

public NinjaDTO criarNinja(NinjaDTO ninjaDTO) {
	NinjaModel ninja = new ninjaMapper.map(ninjaDTO);
	ninja = ninjaRepository.save(ninja);
	return ninjaMapper.map(ninja);
}
```
- E agora precisamos alterar lá no nosso controller
```java
// NinjaController.java

@PostMapping("/criar")
public NinjaDTO criarNinja(@RequestBody NinjaDTO ninja) {
	return ninjaService.criarNinja(ninja);
}
```
- E agora precisamos alterar nos outros métodos, que fazem uso do `NinjaModel`, para usar o `NinjaDTO`
```java
// Listar todos os ninjas cadastrados
public List<NinjaDTO> listarNinjas() {
	List<NinjaModel> ninjas = ninjaRepository.findAll();
	return ninjas.stream()
		.map(ninjaMapper::map)
		.collect(Collectors.toList());
}

// Listar Ninjas por ID
public NinjaDTO listarNinjasPorId(Long id) {
	Optional<NinjaModel> ninjaPorId = ninjaRepository.findById(id);
	return ninjaPorId.map(ninjaMapper::map).orElse(null);
}

// Atualizar ninja
public NinjaDTO atualizarNinja(Long id, NinjaDTO ninjaDTO) {
	Optional<NinjaModel> ninjaExistente = ninjaRepository.findById(id);
	if(ninjaExistente.isPresent()) {
		NinjaModel ninjaAtualizado = ninjaMapper.map(NinjaDTO);
		ninjaAtualizado.setId(id);
		NinjaModel ninjaSalvo = ninjaRepository.save(ninjaAtualizado);
		return ninjaMapper.map(ninjaSalvo);
	}
	
	return null;
}

```
- E agora que atualizamos o nosso `service`, bastamos mudar os tipos para `NinjaDTO` em nosso controller;