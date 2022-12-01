# Git flow from this project:

## Branches

* `master` é a branch principal, onde o código reflete o que está em produção.
* `develop` é a branch de desenvolvimento, onde o código reflete o que está em homologação.
* `feature/*` são branches de features, onde o código reflete o que está sendo desenvolvido.

## Commits

* Commits devem ser pequenos, frequentes e com mensagens claras.
* Não deve haver commits na branch `master`.
* Não deve haver commits na branch `develop`.

## Pull Requests

Pull Request devem ser feitos em duas situacões:

* Quando uma feature estiver pronta para ser integrada ao `develop`. Neste caso o Pull Request deve ser feito da branch `feature/*` para a branch `develop`. A branch `feature/*` deve ser deletada após o merge.
* Quando a branch `develop` estiver pronta para ser integrada ao `master`. Neste caso o Pull Request deve ser feito da branch `develop` para a branch `master`. A branch `develop` não deve ser deletada após o merge.

## Flow

### Desenvolvendo uma feature

1. Crie uma branch a partir da branch `develop` com o nome `feature/*`.
```mermaid
graph LR
A(develop) --> B(feature/*)
```
2. Faça commits nessa branch.
```mermaid
graph LR
A(develop) --> B(feature/*)
B --> C[commits]
```
3. Faça Push dessa branch para o repositório remoto ao final do dia.
```mermaid
graph LR
A(develop) --> B(feature/*)
B --> C[commits]
C --> D(push)
```
4. Ao concluir a feature, faça um Pull Request da branch `feature/*` para a branch `develop`.
```mermaid
graph LR
A(develop) --> B(feature/*)
B --> C[commits]
C --> D(push)
D --> E(Pull Request)
```
5. Deletar a branch `feature/*` após o merge.
```mermaid	
graph LR
A(develop) --> B(feature/*)
B --> C[commits]
C --> D(push)
D --> E(Pull Request)
E --> F(develop)
```

### Enviando uma versão para produção
1. Testar a branch `develop` em homologação.
```mermaid
graph LR
A(develop) --> B(homologação)
```
2. Ao concluir os testes, fazer um Pull Request da branch `develop` para a branch `master`.
```mermaid
graph LR
A(develop) --> B(homologação)
B --> C(Pull Request)
```
3. Revise o Pull Request.
```mermaid
graph LR
A(develop) --> B(homologação)
B --> C(Pull Request)
C --> D(revisão)
```
4. Faça o merge.
```mermaid
graph LR
A(develop) --> B(homologação)
B --> C(Pull Request)
C --> D(revisão)
D --> E(merge)
```
5. Faça o deploy.
```mermaid
graph LR
A(develop) --> B(homologação)
B --> C(Pull Request)
C --> D(revisão)
D --> E(merge)
E --> F(deploy)
```
6. Testar a branch `master` em produção.
```mermaid
graph LR
A(develop) --> B(homologação)
B --> C(Pull Request)
C --> D(revisão)
D --> E(merge)
E --> F(deploy)
F --> G(produção)
```