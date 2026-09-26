Mapa de POPs para uso interno na UBSF Bucarein

## Como editar o mapa

O site publicado (`index.html`) **não tem modo de edição**. O editor é o `editor.html`, que fica no mesmo repositório mas sem nenhum link: o endereço é o do site com `editor.html` no lugar de `index.html` (vale guardar nos favoritos). Localmente, abra o `editor.html` pelo Live Server.

1. Abra o `editor.html`, clique no cadeado e digite a senha.
2. Edite o mapa.
3. Clique no botão de dados e depois em **Publicar**. São baixados dois arquivos: `index.html` (o site, sem modo dev) e `editor.html` (o editor já com o mapa novo).
4. Substitua os dois na raiz do repositório: commit + push, ou, no GitHub, **Add file → Upload files**. Se o navegador baixar como `index (1).html`, corrija o nome antes de enviar.

Regras:

- Mudanças de **código** vão só no `editor.html`; o `index.html` nunca é editado à mão, ele sai do Publicar. (É o mesmo arquivo, sem o atributo `data-editor` e sem o `noindex`.)
- Novos PDFs vão em `pdfs/`, com o nome adicionado em `pdfs/manifest.json`.
- O botão de dados também exporta e importa o mapa em `.json`, para backup.

### Trocar a senha

A senha não fica no código, só o hash SHA-256 dela, no atributo `data-editor` da tag `<html>` do `editor.html`. Para gerar o hash sem deixar a senha no histórico:

```
read -rsp 'Senha nova: ' p; echo; printf '%s' "$p" | sha256sum | cut -d' ' -f1; unset p
```

Use mais que 4 dígitos: o hash de um PIN curto se descobre em instantes. Este é um repositório público, então nada aqui é secreto de verdade; a senha só impede que um visitante ligue o modo de edição sem querer, e nada do que ele fizer chega ao site (só um push muda o site).
