Entity 설정에서, 사용한 annotation 이 있는데, 

lombok.Data; 이다.
@Data

빌드 오류가 났는데, setter 오류임.
이문제는 
file-settings->build,execution,deployment->compiler->annotation processors 
- Enable annotation process (checked)
- Processor path: 에서
- Obtrain Processors from project classpath... 로 변경

이걸로 꽤 시간 낭비함.