# API unificada de Evertec Colombia

La API unificada de Evertec Colombia es un servicio de tipo REST con urls predecibles, orientadas a recursos, que utiliza códigos de respuesta HTTP para indicar los resultados de las operaciones. Utiliza verbos HTTP, comúnmente utilizados por los clientes HTTP tradicionales en el mercado. Soporta [cross-origin resource sharing o CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), lo que le permite interactuar de forma segura con nuestra API desde casi cualquier aplicación del lado del cliente. Utiliza JSON para los valores que representan entradas y salidas, incluidos los posibles errores.

La **API** autentica sus solicitudes al API con claves de API asociadas con una aplicación. Si no incluye su clave al hacer una solicitud al API, o si utiliza una que sea incorrecta,  desactualizada o bloqueada, La **API** devolverá un error.
