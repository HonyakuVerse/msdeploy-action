# 🛠️ MSDeploy WebDeploy Action

Este GitHub Action permite desplegar una aplicación .NET ya publicada usando **MSDeploy (Web Deploy)** desde un runner Windows. Utiliza un archivo `manifest.xml` y `parameters.xml` para una sincronización eficiente y personalizada.

> ✅ Solo se actualizan los archivos modificados gracias a `-useChecksum`.

---

## 📦 Entradas (`inputs`)

| Nombre          | Descripción                                          | Requerido |
|-----------------|------------------------------------------------------|-----------|
| `publish-path`  | Ruta absoluta al directorio de publicación (`publish`) | ✅        |
| `site-name`     | Nombre de la aplicación IIS en el servidor remoto     | ✅        |
| `server`        | Dirección del servidor (ComputerName para MSDeploy)   | ✅        |
| `username`      | Usuario con permisos de publicación                   | ✅        |
| `password`      | Contraseña o token de publicación                     | ✅        |

---

## ✅ Ejemplo de uso

```yaml
- name: Deploy with MSDeploy
  uses: HonyakuVerse/msdeploy-action@v1
  with:
    publish-path: '${{ github.workspace }}\\publish'
    site-name: '${{ vars.WEB_DEPLOY_SITE }}'
    server: '${{ vars.WEB_DEPLOY_SERVER }}'
    username: '${{ vars.WEB_DEPLOY_USER }}'
    password: '${{ secrets.WEB_DEPLOY_KEY }}'
