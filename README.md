# dio-live-cloudfront
Repositório de código para o Live Coding do dia 24/09/2021.

### Serviços utilizados
 - Cloudfront
 - S3
 
### Configurações iniciais

#### Criando o bucket no S3
- AWS Console -> S3 -> Create bucket -> Bucket name [nome único] -> AWS Region [padrão] -> Manter configurações de acesso padrão -> Create bucket
- Acessar o bucket criado -> Upload -> Add files -> Arquivos disponíveis na pasta ```/src``` do repositório -> Upload 

#### COnfigurando o CloudFront

- CloudFront Console -> Create distribution -> Origin domain [seu bucket S3 criado anteriormente] -> Yes use OAI (bucket can restrict access to only CloudFront) -> Create new OAI -> Bucket Policy [Yes, update the bucket policy]
- Viewer protocol policy [Redirect HTTP to HTTPS]
- Cache key and origin requests -> Cache policy and origin request policy (recommended)
- Settings [Use all edge locations (best performance)]
- Create distribution

#### Verificando permissões no S3

- S3 Console -> bucket criado anteriormente -> Permissions -> verificar as permissões atualizadas nas políticas de acesso

#### Acessando pelo browser

https://<meu_dominio>.cloudfront.net/index.html

#### Configurando a página ```index.html``` como default

- CloudFront Console -> selecionar a distribuição criada -> General -> Settings -> Edit
- Default root object - optional [index.html]

### Configurações Extras

#### Configurando páginas de erro

- CloudFront Console -> selecionar a distribuição criada -> Error pages -> Create custom error response
- HTTP error code [403]
- Customize error response -> Response page path [/404.html] -> HTTP Response code [404 Not found]
