# Central Macatuba — Documentação da API Pública

Repositório da documentação interativa da **API pública da Central Macatuba**, utilizando Swagger UI e a especificação OpenAPI.

> Este projeto documenta exclusivamente a API pública. Não inclua especificações, endpoints, credenciais, tokens ou detalhes internos da API privada.

## Objetivo

Disponibilizar uma interface web estática para que desenvolvedores possam consultar as operações, parâmetros, exemplos e respostas descritos no contrato OpenAPI e, quando permitido pela API, experimentar requisições.

## Especificação OpenAPI

O arquivo `openapi.json` deste repositório deve ser uma **cópia fiel** do arquivo oficial mantido em:

- Repositório de origem: [centralmacatuba/api](https://github.com/centralmacatuba/api)
- Caminho de origem: `publica/openapi.json`
- URL pública da especificação original: <https://publica.api.centralmacatuba.qzz.io/openapi.json>

A interface Swagger UI deve carregar **o arquivo local `openapi.json` deste mesmo repositório**, e não buscar a especificação remota durante o uso normal. Assim, a interface documenta exatamente a cópia versionada junto dela.

Quando o contrato da API for atualizado, confira as alterações na origem e atualize a cópia local de forma explícita. Não modifique, resuma nem recrie manualmente o contrato para fazê-lo combinar com a interface.

A especificação atualmente conhecida usa OpenAPI `3.1.2` e identifica o servidor público canônico como `https://publica.api.centralmacatuba.qzz.io`. Confirme esses valores no arquivo de origem antes de atualizar a cópia.

## Hospedagem pretendida

A hospedagem pretendida é o **GitHub Pages**, usando a publicação a partir de uma branch/configuração do próprio GitHub, sem exigir um workflow personalizado do GitHub Actions.

Endereço esperado, após habilitar e configurar o GitHub Pages:

<https://centralmacatuba.github.io/api-publica-docs/>

O endereço só estará ativo depois de a publicação ser configurada no GitHub.

## Princípios do projeto

- Priorizar arquivos estáticos, simplicidade, acessibilidade e compatibilidade com navegadores modernos.
- Usar uma versão estável e fixada do Swagger UI, sem dependências desnecessárias.
- Não exigir servidor próprio, banco de dados, processo de build ou segredos para servir a interface.
- Não adicionar credenciais, chaves de API, tokens, dados privados ou informações sensíveis.
- Não inventar, alterar ou remover operações do contrato OpenAPI.
- Tratar o arquivo `openapi.json` local como a especificação usada pela interface.
- Documentar claramente qualquer configuração manual necessária para habilitar o GitHub Pages.
- Não criar GitHub Actions só para publicar o site.
- Não criar Pull Request até que isso seja solicitado explicitamente.

## Desenvolvimento

Consulte o prompt de implementação fornecido pelo responsável pelo projeto para as instruções detalhadas de criação da interface, atualização da cópia OpenAPI, validações e trabalho em branch separada.
