# Central Macatuba — Documentação da API Pública

Este repositório publica uma interface estática e interativa com **Swagger UI** para consultar exclusivamente o contrato da **API pública** da Central Macatuba. Não contém documentação da API privada.

## Conteúdo

- `index.html`: página da documentação.
- `openapi.json`: cópia local e versionada da especificação OpenAPI usada pelo Swagger UI.
- `styles.css`: estilos da página.
- `.nojekyll`: impede que o GitHub Pages aplique o processamento Jekyll.

A interface referencia a especificação por caminho relativo (`./openapi.json`), adequado ao endereço de projeto `/api-publica-docs/`. A interface não consulta a URL remota para carregar o contrato.

## Origem e atualização da especificação

A cópia incluída foi obtida de:

- Repositório: [centralmacatuba/api](https://github.com/centralmacatuba/api)
- Arquivo: [`publica/openapi.json` na branch `fix/openapi-php-consistency`](https://github.com/centralmacatuba/api/blob/fix/openapi-php-consistency/publica/openapi.json)
- Blob SHA-1 do arquivo de origem e da cópia: `4cbf791bb644059b229aece4e48b4fe8235b4522`
- Versão OpenAPI declarada: `3.1.2`
- Versão do contrato (`info.version`): `1.1.0`
- Servidor canônico documentado: `https://publica.api.centralmacatuba.qzz.io`

**Observação de procedência:** no momento desta implementação, `publica/openapi.json` não foi encontrado na branch padrão `principal` do repositório `centralmacatuba/api`. Por isso, a cópia foi feita da branch de trabalho explicitamente indicada, `fix/openapi-php-consistency`, que contém o arquivo. Confirme que esse contrato é o aprovado antes de publicar a documentação para usuários finais. Nenhum arquivo do repositório de origem foi alterado.

Para atualizar a cópia, revise primeiro o contrato pretendido no repositório de origem e então copie o arquivo integralmente, sem edição manual. Registre a branch ou commit de origem e compare a cópia byte a byte (ou por hash) com o arquivo original. Não há sincronização automática nem workflow de GitHub Actions neste projeto.

## Swagger UI e dependências

A página utiliza Swagger UI **5.33.3**, distribuição oficial `swagger-ui-dist`, referenciada por versão fixa no jsDelivr:

- CSS: `https://cdn.jsdelivr.net/npm/swagger-ui-dist@5.33.3/swagger-ui.css`
- JavaScript: `https://cdn.jsdelivr.net/npm/swagger-ui-dist@5.33.3/swagger-ui-bundle.js`
- Projeto e licença: [swagger-api/swagger-ui](https://github.com/swagger-api/swagger-ui), licença Apache-2.0.

Esta escolha mantém o repositório pequeno e dispensa etapa de build, mas depende de conexão com jsDelivr para carregar a interface Swagger UI. Se o CDN estiver indisponível, o HTML e o JSON local ainda podem ser acessados, porém a interface interativa não será renderizada. Os arquivos de Swagger UI não estão incluídos localmente no repositório.

## Visualização local

Sirva a pasta por um servidor HTTP estático e abra o endereço local no navegador. Por exemplo, com Python instalado:

```sh
python -m http.server 8000
```

Acesse <http://localhost:8000/>. Não é necessário PHP, Node.js, banco de dados ou servidor de aplicação. Abrir o HTML diretamente por `file://` pode impedir que o navegador carregue `openapi.json` devido às restrições de origem.

## Configurar o GitHub Pages

O endereço esperado é <https://centralmacatuba.github.io/api-publica-docs/>. Ele só estará publicado depois de o proprietário habilitar a configuração:

1. Abra o repositório `centralmacatuba/api-publica-docs` no GitHub.
2. Entre em **Settings → Pages**.
3. Em **Build and deployment**, escolha **Deploy from a branch**.
4. Selecione a branch que contém a implementação (`feat/swagger-ui-public-api`) e a pasta `/(root)`, caso deseje testar esta branch antes de integrar as alterações.
5. Salve a configuração e aguarde o GitHub Pages concluir a publicação.
6. Depois que a implementação for aprovada e incorporada à branch principal, ajuste a fonte de publicação para a branch principal e `/(root)`, se essa for a configuração desejada.

Nenhuma configuração de Pages foi alterada durante esta tarefa e a publicação não foi verificada nem afirmada como ativa. Não há domínio personalizado nem workflow de publicação neste repositório.

## Confirmar que a cópia local foi carregada

Abra a documentação e, nas ferramentas de desenvolvedor do navegador, confira a aba **Network/Rede**:

- Deve existir uma requisição bem-sucedida para `openapi.json` sob o mesmo caminho do site (por exemplo, `/api-publica-docs/openapi.json`).
- A requisição da especificação não deve apontar para `publica.api.centralmacatuba.qzz.io/openapi.json`.
- O carregamento do CSS e do JavaScript do Swagger UI ocorrerá em `cdn.jsdelivr.net`.

Também é possível abrir diretamente <https://centralmacatuba.github.io/api-publica-docs/openapi.json> após a publicação estar ativa.

## Try it out, CORS e limites

O Swagger UI está configurado para habilitar `Try it out` apenas para os métodos `GET` e `HEAD`, que são os métodos documentados na cópia atual. As requisições são enviadas diretamente ao servidor definido na especificação; não existe proxy nesta documentação e nenhuma chave ou credencial é adicionada pelo navegador.

O site do GitHub Pages e a API possuem origens diferentes. O navegador só permitirá que o JavaScript leia as respostas se o servidor da API enviar cabeçalhos CORS compatíveis com a origem do site. Carregar a interface e o contrato não comprova que CORS está habilitado. Se o `Try it out` falhar por CORS, será necessário avaliar separadamente a configuração CORS do servidor da API; este repositório não altera a API para contornar essa restrição.

A API pode ainda aplicar regras de acesso, limites, disponibilidade ou validações próprias. A interface não inventa credenciais e não deve ser usada para testar operações destrutivas. A API privada está fora do escopo deste repositório.
