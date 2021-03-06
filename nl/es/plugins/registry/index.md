---



copyright:

  years: 2017

lastupdated: "2017-08-30"


---

{:codeblock: .codeblock}
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# {{site.data.keyword.registrylong_notm}}CLI
{: #containerregcli}

{{site.data.keyword.registrylong}} CLI es un plugin que permite gestionar su registro y sus recursos de su cuenta.
{: shortdesc}

**Requisitos previos**
* Antes de ejecutar mandatos de registro, inicie una sesión en {{site.data.keyword.Bluemix_short}} con el mandato `bs login` para generar una señal de acceso de {{site.data.keyword.Bluemix_short}} y autenticar la sesión.

Para obtener información sobre la utilización de la interfaz de línea de mandatos de la CLI de {{site.data.keyword.registrylong}}, consulte [Configuración de un registro de imágenes privado](../../../services/Registry/index.html).

<table summary="Gestión del registro de contenedores">
<caption>Tabla 1. Mandatos para gestionar {{site.data.keyword.registryshort}} en {{site.data.keyword.Bluemix_short}}
</caption>
 <thead>
 <th colspan="5">Mandatos para gestionar el registro</th>
 </thead>
 <tbody>
 <tr>
 <td>[bx cr api](#bx_cr_api)</td>
 <td>[bx cr info](#bx_cr_info)</td>
 <td>[bx cr image-inspect](#bx_cr_image_inspect)</td>
 <td>[bx cr image-list (bx cr images)](#bx_cr_image_list)</td>
 <td>[bx cr image-rm](#bx_cr_image_rm)</td>
 </tr>
 <tr>
 <td>[bx cr login](#bx_cr_login)</td>
 <td>[bx cr namespace-add](#bx_cr_namespace_add)</td>
 <td>[bx cr namespace-list (bx cr namespaces)](#bx_cr_namespace_list)</td>
 <td>[bx cr namespace-rm](#bx_cr_namespace_rm)</td>
 <td>[bx cr plan](#bx_cr_plan)</td>
 </tr>
 <tr>
 <td>[bx cr plan-upgrade](#bx_cr_plan_upgrade)</td>
 <td>[bx cr pricing](#bx_cr_pricing)</td>
 <td>[bx cr quota](#bx_cr_quota)</td>
 <td>[bx cr quota-set](#bx_cr_quota_set)</td>
 <td>[bx cr token-add](#bx_cr_token_add)</td>
 </tr>
 <tr>
 <td>[bx cr token-get](#bx_cr_token_get)</td>
 <td>[bx cr token-list (bx cr tokens)](#bx_cr_token_list)</td>
 <td>[bx cr token-rm](#bx_cr_token_rm)</td>
 <td>[bx cr vulnerability-assessment (bx cr va)](#bx_cr_va)</td>
 </tr>
 </tbody></table>



## bx cr api
{: #bx_cr_api}

Devuelve los detalles sobre el punto final de la API de registro sobre el que se ejecutan los mandatos.

```
bx cr api
```
{: codeblock}


## bx cr info
{: #bx_cr_info}

Visualiza el nombre y la cuenta del registro en el que ha iniciado una sesión.

```
bx cr info
```
{: codeblock}


## bx cr image-inspect
{: #bx_cr_image_inspect}

Visualiza detalles sobre una imagen específica.

```
bx cr image-inspect [--format FORMAT] IMAGE [IMAGE...]
```
{: codeblock}

**Parámetros**

<dl>
<dt>--format FORMAT</dt>
<dd>(Opcional) Formatear los elementos de salida mediante una plantilla de Go. 

Para obtener más información, consulte [Visualización de información sobre las imágenes](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
<dt>IMAGE</dt>
<dd>Vía de acceso completa de registro de {{site.data.keyword.Bluemix_short}} a la imagen que desea examinar, que se encuentra en formato `namespace/image:tag`. Si no se especifica ninguna etiqueta en la vía de acceso de imagen, se examina la imagen etiquetada como `latest`. Puede examinar varias imágenes creando una lista de cada vía de acceso privada al registro de {{site.data.keyword.Bluemix_short}} en el mandato con un espacio entre cada vía de acceso.</dd>
</dl>


## bx cr image-list (bx cr images)
{: #bx_cr_image_list}

Visualiza todas las imágenes de su cuenta de {{site.data.keyword.Bluemix_short}}.

```
 bx cr image-list [--no-trunc] [-q, --quiet] [--include-ibm] [--format FORMAT]
```
{: codeblock}

**Parámetros**
<dl>
<dt>--no-trunc</dt>
<dd>(Opcional) No truncar los resúmenes de imagen.</dd>
<dt>-q, --quiet</dt>
<dd>(Opcional) Cada imagen se lista en el formato: `repository:tag`.</dd>
<dt>--include-ibm</dt>
<dd>(Opcional) Incluye en la salida las imágenes públicas proporcionadas por IBM. Sin esta opción, de forma predeterminada solo se muestran en la lista las imágenes privadas.</dd>
<dt>--format FORMAT</dt>
<dd>(Opcional) Formatear los elementos de salida mediante una plantilla de Go. 

Para obtener más información, consulte [Visualización de información sobre las imágenes](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>


## bx cr image-rm
{: #bx_cr_image_rm}

Suprime de su registro una o varias de las imágenes especificadas.

```
bx cr image-rm IMAGE [IMAGE...]
```
{: codeblock}

**Parámetros**
<dl>
<dt>IMAGE</dt>
<dd>Vía de acceso de registro de {{site.data.keyword.Bluemix_short}} a la imagen que desea eliminar, en el formato `namespace/image:tag`. Si no se especifica ninguna etiqueta en la vía de acceso de la imagen, de forma predeterminada se suprime la imagen etiquetada como `latest`. Puede suprimir varias imágenes creando una lista de cada vía de acceso privada al registro de {{site.data.keyword.Bluemix_short}} en el mandato con un espacio entre cada vía de acceso.</dd>
</dl>


## bx cr login
{: #bx_cr_login}

Este mandato ejecuta el mandato `docker login` sobre el registro. Se necesita el mandato `docker login` para poder ejecutar los mandatos `docker push` o `docker pull` para el registro. Este mandato no es necesario para ejecutar otros mandatos `bx cr`. Si Docker no está instalado, este mandato devuelve un mensaje de error.

```
bx cr login
```
{: codeblock}


## bx cr namespace-add
{: #bx_cr_namespace_add}

Añade un espacio de nombres a su cuenta {{site.data.keyword.Bluemix_short}}.

```
bx cr namespace-add NAMESPACE
```
{: codeblock}

**Parámetros**
<dl>
<dt>NAMESPACE</dt>
<dd>El espacio de nombres que desea añadir. El espacio de nombres debe ser exclusivo entre todas las cuentas de {{site.data.keyword.Bluemix_short}} en la misma región.</dd>
</dl>


## bx cr namespace-list (bx cr namespaces)
{: #bx_cr_namespace_list}

Visualiza todos los espacios de nombres cuyo propietario es su cuenta de {{site.data.keyword.Bluemix_short}}.

```
bx cr namespace-list
```
{: codeblock}


## bx cr namespace-rm
{: #bx_cr_namespace_rm}

Elimina un espacio de nombres de su cuenta de {{site.data.keyword.Bluemix_short}}. Las imágenes en este espacio de nombres se suprimen cuando se elimina el espacio de nombres.

```
bx cr namespace-rm NAMESPACE
```
{: codeblock}

**Parámetros**
<dl>
<dt>NAMESPACE</dt>
<dd>El espacio de nombres que desea eliminar.</dd>
</dl>



## bx cr plan
{: #bx_cr_plan}

Visualiza su plan de precios.

```
bx cr plan
```
{: codeblock}


## bx cr plan-upgrade
{: #bx_cr_plan_upgrade}

Actualiza desde el plan gratuito al estándar.

Para obtener más información sobre los planes, consulte [Planes de registro](../../../services/Registry/registry_overview.html#registry_plans).

```
bx cr plan-upgrade standard
```
{: codeblock}


## bx cr pricing
{: #bx_cr_pricing}

Este mandato se ha eliminado. Puede utilizar la calculadora de tarifas para calcular su coste estimado, consulte [Estimación de costes para IBM Bluemix Container Registry](../../../services/Registry/registry_overview.html#registry_plan_billing#task_02).


## bx cr quota
{: #bx_cr_quota}

Visualiza sus cuotas actuales de tráfico y almacenamiento, así como información de utilización relacionada con las mismas.

```
bx cr quota
```
{: codeblock}


## bx cr quota-set
{: #bx_cr_quota_set}

Modifica la cuota especificada.

```
bx cr quota-set [--traffic VALUE] [--storage VALUE]
```
{: codeblock}

**Parámetros**
<dl>
<dt>--traffic VALUE</dt>
<dd>(Opcional) Cambia su cuota de tráfico al valor que especifique. La operación falla si no está autorizado a establecer cuotas de tráfico, o si establece un valor por encima del que permite su plan de precios actual.</dd>
<dt>--storage VALUE</dt>
<dd>(Opcional) Cambia su cuota de almacenamiento al valor que especifique. La operación falla si no está autorizado a establecer cuotas de almacenamiento, o si establece un valor por encima del que permite su plan de precios actual.</dd>
</dl>


## bx cr token-add
{: #bx_cr_token_add}

Añade una señal que sirve para controlar el acceso a un registro.

```
bx cr token-add [--description VALUE] [-q, --quiet] [--non-expiring] [--readwrite]
```

{: codeblock}


**Parámetros**
<dl>
<dt>--description VALUE</dt>
<dd>(Opcional) Especifica el valor como una descripción para la señal, que se visualiza al ejecutar `bx cr token-list`. Si IBM Bluemix Container Service ha creado su señal de forma automática, la descripción se establece en su nombre clúster Kubernetes. En este caso, la señal se elimina de forma automática al eliminar su clúster.</dd>
<dt>-q, --quiet</dt>
<dd>(Opcional) Visualiza únicamente la señal, sin ningún texto a su alrededor.</dd>
<dt>--non-expiring</dt>
<dd>(Opcional) Crea una señal con un acceso que no caduca. Si no se establece este parámetro, de forma predeterminada el acceso con la señal caduca después de 24 horas.</dd>
<dt>--readwrite</dt>
<dd>(Opcional) Crea una señal que otorga acceso de lectura y escritura. Sin esta opción, de forma predeterminada el acceso es de solo lectura.</dd>
</dl>


## bx cr token-get
{: #bx_cr_token_get}

Recupera la señal especificada desde el registro.

```
bx cr token-get TOKEN
```

{: codeblock}

**Parámetros**
<dl>
<dt>TOKEN</dt>
<dd>(Opcional) Identificador exclusivo de la señal que desea recuperar.</dd>
</dl>


## bx cr token-list (bx cr tokens)
{: #bx_cr_token_list}

Visualiza todas las señales que existen para su cuenta de {{site.data.keyword.Bluemix_short}}.

```
bx cr token-list --format FORMAT
```
{: codeblock}

**Parámetros**
<dl>
<dt>--format FORMAT</dt>
<dd>(Opcional) Formatear los elementos de salida mediante una plantilla de Go. 

Para obtener más información, consulte [Visualización de información sobre las imágenes](../../../services/Registry/registry_cli_reference.html#registry_cli_listing).

</dd>
</dl>

## bx cr token-rm
{: #bx_cr_token_rm}

Elimina una o varias de las señales especificadas.

```
bx cr token-rm TOKEN [TOKEN...]
```
{: codeblock}

**Parámetros**
<dl>
<dt>TOKEN</dt>
<dd>(Opcional) TOKEN puede ser la propia señal, o el identificador exclusivo de la señal, tal como se muestra en `bx cr token-list`. Es posible especificar varias señales separándolas con espacios en blanco.</dd>
</dl>


## bx cr vulnerability-assessment (bx cr va)
{: #bx_cr_va}

Visualiza un informe de valoración de vulnerabilidad para una imagen.

```
bx cr vulnerability-assessment IMAGE [IMAGE...]
```
{: codeblock}

**Parámetros**
<dl>
<dt>IMAGE</dt>
<dd>Vía de acceso de registro de {{site.data.keyword.Bluemix_short}}, en el formato `namespace/image:tag`, a la imagen de la que desea informar. El informe indica si la imagen tiene vulnerabilidades de empaquetamiento conocidas. Se da soporte a los sistemas operativos siguientes:

<ul>

<li>Alpine</li>
<li>CentOS</li>
<li>Debian</li>
<li>Red Hat Enterprise Linux (RHEL)</li>
<li>Ubuntu</li>
</ul>

Para obtener más información, consulte [Revisión la seguridad de imágenes](../../../services/Registry/registry_images_.html#registry_security_checking).

</dd>

</dl>

