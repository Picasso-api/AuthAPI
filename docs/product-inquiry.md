# Consulta de productos de un afiliado

Transacciones administrativas de consulta de productos financieros de un afiliado.

## Consultar productos disponibles de un afiliado

Obtiene la informaci�n resumida de las cuentas o productos asociados a un afiliado.

> Cuando el afiliado no tiene productos asociados la respuesta ser� una lista vac�a.

| Verbo | Endpoint                                      | Requiere autenticaci�n |
| :---: | --------------------------------------------- | :--------------------: |
| GET  | https://[host]:[port]/inquiry |          [ Si ]           |

*host*: Nombre de dominio o direcci�n IP del servicio de transacciones.  
*port*: N�mero del puerto del servicio de transacciones.

### Valores de la solicitud

Campo | Tipo de dato | Descripci�n | Requerido
:---: | :----------: | ----------- | :-------:
Tipo de documento | `string` | Tipo de documento del afiliado. Cualquier valor de la columna **Acr�nimo** en el dominio de los [Tipos de documento](product-inquiry.md#docType). Valor esperado en la URL sin corchetes. | [x]
N�mero de documento | `string` | N�mero de documento del afiliado. Valor esperado en la URL sin corchetes. | [x]


### Valores de la respuesta

Campo | Tipo de dato | Descripci�n
:---: | :----------: | -----------
Identificador | `string` | Identificador un�voco de la cuenta.
Saldo | `decimal` | Valor del saldo actual de la cuenta.
N�mero de cuenta | `string` | N�mero enmascarado de la cuenta.
Orden | `int` | Orden del elemento para visualizar en interfaz de usuario.
Producto | `string` | Nombre asignado al producto.
Propiedades | `list` | Es un conjunto de propiedades o atributos que representan informaci�n adicional de la cuenta. [Propiedades de una cuenta](product-inquiry.md#accountProperties)
Origen | `int` | Define los sistemas reconocidos desde donde se originaron los datos de la cuenta. [Tipos de sistemas](product-inquiry.md#subsystems)
Identificador de cuenta origen | `string` | Identificador de la cuenta que se utilizar� en procesos transaccionales

#### Propiedades de una cuenta

<div id="accountProperties"></div>

Las propiedades representan informaci�n resumida por alguna caracter�stica de la cuenta.

Campo | Tipo de dato | Descripci�n
:---: | :----------: | -----------
Nombre de atributo | `string` | Nombre o etiqueta para visualizar el contenido del atributo en interfaz de usuario.
Identificador de atributo | `string` | Identificador interno del atributo.
Valor | `string` | Valor asociado con el atributo.

<div class="admonition warning">
   <p class="first admonition-title">Atenci�n</p>
   <p class="last">El conjunto de propiedades o atributos de una cuenta pueden variar de acuerdo con el sistema de origen del producto.</p>
</div>

#### Tipos de sistemas

<div id="subsystems"></div>

Valor | Nombre | Descripci�n
:---: | :----: | -----------
`0` | Tup | El origen de la informaci�n es el sistema de administraci�n de tarjetas d�bito **TUP**.
`1` | Bancor | El origen de la informaci�n es sistema de administraci�n de cartera **BANCOR**.
`2` | Ninguno | No hay un sistema definido. La informaci�n se puede utilizar con la finalidad de comprobar el funcionamiento del servicio, mientras se finalizan los acuerdos comerciales que permitan a los afiliados del API, consumir la informaci�n real de los sistemas transaccionales. 

## Consultar saldos de una cuenta

Obtiene los saldos (balances) detallados de una cuenta d�bito.

> Cuando la cuenta del afiliado no tiene saldos asociados la respuesta ser� una lista vac�a.

| Verbo | Endpoint                                      | Requiere autenticaci�n |
| :---: | --------------------------------------------- | :--------------------: |
| GET  | https://[host]:[port]/inquiry |          [ Si ]           |

*host*: Nombre de dominio o direcci�n IP del servicio de transacciones.  
*port*: N�mero del puerto del servicio de transacciones.

### Valores de la solicitud

Campo | Tipo de dato | Descripci�n | Requerido
:---: | :----------: | ----------- | :-------:
Tipo de documento | `string` | Tipo de documento del afiliado. Cualquier valor de la columna **Acr�nimo** en el dominio de los **[Tipos de documento](product-inquiry.md#docType)**. Valor esperado en la URL sin corchetes. | [x]
N�mero de documento | `string` | N�mero de documento del afiliado. Valor esperado en la URL sin corchetes. | [x]
Identificador de cuenta | `string` | Identificador de la cuenta para la que se obtienen los saldos (Corresponde con el valor del atributo `Identificador` de la respuesta de la consulta de cuentas). Valor esperado en la URL sin corchetes. | [x]


### Valores de la respuesta

Campo | Tipo de dato | Descripci�n
:---: | :----------: | -----------
Saldo | `decimal` | Valor del saldo actual de la cuenta.
N�mero de cuenta | `string` | N�mero enmascarado de la cuenta.
Identificador de cuenta origen | `string` | Identificador de la cuenta que se utilizar� en procesos transaccionales.
Identificador tipo de cuenta | `string` | Identificador del tipo de cuenta.
Nombre tipo de cuenta | `string` | Nombre del tipo de cuenta.

## Consultar movimientos de una cuenta

Obtiene la informaci�n de transacciones financieras realizadas en una cuenta.

> Cuando la cuenta no presenta movimientos la respuesta ser� una lista vac�a.

| Verbo | Endpoint                                      | Requiere autenticaci�n |
| :---: | --------------------------------------------- | :--------------------: |
| GET  | https://[host]:[port]/inquiry |          [ Si ]           |

*host*: Nombre de dominio o direcci�n IP del servicio de transacciones.  
*port*: N�mero del puerto del servicio de transacciones.

### Valores de la solicitud

Campo | Tipo de dato | Descripci�n | Requerido
:---: | :----------: | ----------- | :-------:
Tipo de documento | `string` | Tipo de documento del afiliado. Cualquier valor de la columna **Acr�nimo** en el dominio de los **[Tipos de documento](product-inquiry.md#docType)**. Valor esperado en la URL sin corchetes. | [x]
N�mero de documento | `string` | N�mero de documento del afiliado. Valor esperado en la URL sin corchetes. | [x]
Identificador de cuenta | `string` | Identificador de la cuenta para la que se obtienen los saldos (Corresponde con el valor del atributo `Identificador` de la respuesta de la consulta de cuentas). Valor esperado en la URL sin corchetes. | [x]
Identificador tipo de cuenta | `string` | Identificador del tipo de cuenta. **Aplica para las cuentas d�bito**. (Corresponde con el valor del atributo `Identificador` de la respuesta de la consulta de cuentas) Puede usar asterisco (`*`) para consultar los �ltimos movimientos de todo el producto. Valor esperado en la URL sin corchetes. |


### Valores de la respuesta

Campo | Tipo de dato | Descripci�n
:---: | :----------: | -----------
Identificador tipo de cuenta | `string` | Identificador del tipo de cuenta que afect� el movimiento/transacci�n.
Nombre tipo de cuenta | `string` | Nombre del tipo de cuenta que afect� el movimiento/transacci�n.
Monto | `decimal` | Valor por el que se realiz� el movimiento/transacci�n.
Comercio | `string` | Nombre del comercio donde se realiz� el movimiento/transacci�n.
Naturaleza contable | `int` | Define la naturaleza contable de la transacci�n financiera. **[Tipos de categoria](product-inquiry.md#categories)**
Fecha | `datetime` | Fecha y hora en que se realiz� el movimiento/transacci�n.
Nombre movimiento | `string` | Nombre que representa el tipo de movimiento/transacci�n.
C�digo tipo de movimiento | `string` | C�digo que representa el tipo de movimiento/transacci�n.

#### Tipos de categoria

<div id="categories"></div>

Valor | Nombre | Descripci�n
:---: | :----: | -----------
`0` | D�bito | La operaci�n es de tipo d�bito.
`1` | Cr�dito | La operaci�n es de tipo cr�dito.

## Anexos

<a name="Tipo de documentos"></a> 
### Tipos de documento

<div id="docType"></div>

Acr�nimo | Descripci�n
:------: | -----------
CC | C�dula de Ciudadan�a
NIT | N�mero de Identificaci�n Tributaria
TI | Tarjeta de Identidad
CE | C�dula de Extranjer�a
PAS | Pasaporte
CL | Celular

## Informaci�n relacionada

- [Solicitar un token de autenticaci�n](JWT-Request.md)
- [Mensajes de respuesta en Aspen](Responses.md)
