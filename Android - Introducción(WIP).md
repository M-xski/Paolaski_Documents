## Programación Multimedia y Dispositivos Móviles

> Software: Android Studio	Iconos: Material Design



:black_circle: **Enlaces:**

- [Android Developer · Guide](https://developer.android.com)
  - [Manifest](https://developer.android.com/guide/topics/manifest/manifest-element.html)
  - [Estilos y Temas](https://developer.android.com/guide/topics/ui/themes.html)
- [Material Design · Icons](https://materialdesignicons.com/)



#### :black_circle: Índice

[Estructura de una Aplicación Android](#estructura-de-una-aplicación-android)

[Android Manifest](#manifest)

[Activity](#activity)



#### Estructura de una aplicación Android

- /manifests :heavy_minus_sign: Contiene toda la información de nuestra app, así como metadatos.
- /java :heavy_minus_sign: Contiene todo el código lógico de la app.
- /res :heavy_minus_sign: Resources
  - /layout :heavy_minus_sign: Los layouts, vistas de la app que verá el usuario. 
  - /drawable :heavy_minus_sign: Resource de imágenes de la aplicación.
  - /mimap :heavy_minus_sign: Resource de imágenes que usa la aplicación. 
  - /values :heavy_minus_sign: Contiene xml con valores reutilizables en la app.
    - colors.xml, values.xml, style.xml



### Manifest

Un archivo `AndroidManifest.xml` contiene toda la información de nuestra aplicación, metadatos, declaración de activities, etc. Por defecto encontramos:

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.pmdm.actividadesandroid">
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".Actividad01">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
```

Dentro de `<application>` puede contener: `<activity>`,`<activity-alias>`,`<meta-data>`,`<service>`,`<receiver>`,`<provider>`,`<uses-library>`. Y podemos encontrar dependiendo de cada aplicación los siguientes atributos:

```xml
<application android:allowTaskReparenting=["true" | "false"] 
                 android:allowBackup=["true" | "false"]
                 android:allowClearUserData=["true" | "false"]
                 android:backupAgent="string"
                 android:backupInForeground=["true" | "false"]
                 android:banner="drawable resource"
                 android:debuggable=["true" | "false"]
                 android:description="string resource"
                 android:directBootAware=["true" | "false"]
                 android:enabled=["true" | "false"]
                 android:extractNativeLibs=["true" | "false"]
                 android:fullBackupContent="string"
                 android:fullBackupOnly=["true" | "false"]
                 android:hasCode=["true" | "false"]
                 android:hardwareAccelerated=["true" | "false"]
                 android:icon="drawable resource"
                 android:isGame=["true" | "false"]
                 android:killAfterRestore=["true" | "false"]
                 android:largeHeap=["true" | "false"]
                 android:label="string resource"
                 android:logo="drawable resource"
                 android:manageSpaceActivity="string"
                 android:name="string"
                 android:networkSecurityConfig="xml resource"
                 android:permission="string"
                 android:persistent=["true" | "false"]
                 android:process="string"
                 android:restoreAnyVersion=["true" | "false"]
                 android:requiredAccountType="string"
                 android:resizeableActivity=["true" | "false"]
                 android:restrictedAccountType="string"
                 android:supportsRtl=["true" | "false"]
                 android:taskAffinity="string"
                 android:testOnly=["true" | "false"]
                 android:theme="resource or theme"
                 android:uiOptions=["none" | "splitActionBarWhenNarrow"]
                 android:usesCleartextTraffic=["true" | "false"]
                 android:vmSafeMode=["true" | "false"] >
    </application>
```

> **default** por defecto

allowTaskReparenting=["true" | "**false**"] :heavy_minus_sign: Define si la actividad puede pasar de la tarea que la inició a la tarea con la que tiene afinidad cuando dicha tarea se traiga a primer plano la próxima vez (“`true`” si es posible y “`false`” si debe permanecer con la tarea que la inició).

allowBackup=["**true**" | "false"] :heavy_minus_sign: Define si guarda el estado de la aplicación, al salir y volver a la aplicación la restaurará tal cual estaba antes de salir.

allowClearUserData=["**true**" | "false"] :heavy_minus_sign: Define los permisos de la aplicación para resetear los datos del usuario (ajustes y preferencias personalizables).

backupAgent="string" :heavy_minus_sign: Implementa el agente de backup, subclase de BackupAgent.

backupInForeground=["true" | "false"] :heavy_minus_sign: Indica si las operaciones de AutoBackup puede lanzarse en la app incluso si la app esta en un estado de segundo plano equivalente. (Un ejemplo sería un reproductor de música, al salir de la app seguiría sonando. `startForeground()`)

banner="drawable resource"  :heavy_minus_sign: Define un banner que sustituye el banner para todas las activities, si se quiere implementar en una sola activity, se definirá en `<activity>`.

debuggable=["true" | "**false**"] :heavy_minus_sign: Si la aplicación puede realizar debug. 

description="string resource" :heavy_minus_sign: Texto con información sobre la aplicación, el usuario puede leerlo. Debe ser mayor y más descriptivo que un label. <u>Debe ser definido con un string</u>.

directBootAware=["true" | "**false**"]  :heavy_minus_sign: Si la aplicación puede correr antes de que el usuario desbloqueé el dispositivo. 

enabled=["**true**" | "false"] :heavy_minus_sign: Define si el sistema puede o no crear instancias de componentes de la aplicación. Si es verdadero, cada componente determina si esta habilitado o no. 

extractNativeLibs=["**true**" | "false"] :heavy_minus_sign: Determina si el package installer extrae las librerías nativas desde la APK a los archivos del sistema. Si se determina como false, las librerías nativas deben estar almacenadas y descomprimidas en el APK.

fullBackupContent="string" :heavy_minus_sign: Dirige hacia un archivo XML que contiene las reglas para un backup completo. Opcional.

fullBackupOnly=["true" | "**false**"] :heavy_minus_sign: Indica si puede o no usarse el Auto Backup en dispositivos donde esté disponible. Si se establece true, la app podrá realizar autobackups cuando estén instaladas en un dispositivo Android 6.0 en adelante. En dispositivos anteriores será ignorado.

android:hasCode=["**true**" | "false"] :heavy_minus_sign: Define si la aplicación contiene algún codigo. Si el valor es falso, el sistema no intentará cargar ningún codigo cuando está lanzando componentes.

hardwareAccelerated=["**true**" | "false"] :heavy_minus_sign: Establece la aceleración de hardware.

icon="drawable resource" :heavy_minus_sign: Establece el icono por defecto de la aplicación. Tiene que referenciarse en drawable.

isGame=["true" | "**false**"] :heavy_minus_sign: Si la app es un juego o no. 
killAfterRestore=["**true**" | "false"] :heavy_minus_sign: Define si la aplicación en cuestión debería terminar después de que la configuración haya sido restaurada tras un reinicio del sistema. En true significa que después de que acabe el proceso tras el reinicio del sistema, terminará. 

largeHeap=["true" | "false"] :heavy_minus_sign: Evitar usarlo. Disminuye el riesgo de sacar el error `OutOfMemoryError`, pero puedes perder algunos frames, lo que puede hacer que se cuelgue la app.

label="string resource" :heavy_minus_sign: Un label que el usuario podrá leer contiene una descripción breve de la aplicación, debe ser referenciado por un string. 

logo="drawable resource" :heavy_minus_sign: Define el logo para las activities.

 manageSpaceActivity="string" :heavy_minus_sign: Define el nombre de una activity subclase que el sistema puede lanzar para que los usuarios se hagan cargo de la memoria que tiene ocupada la app en el dispositivo. Debe declararse con un elemento `<activity>`. 

name="string" :heavy_minus_sign: Define el nombre.

networkSecurityConfig="xml resource" :heavy_minus_sign: Especifica el nombre de un fichero xml que contiene la configuración de seguridad de la red. (Añadido en la API 24).

permission="string" :heavy_minus_sign: Restricción que limita el acceso a una parte del código o a datos en el dispositivo, se impone para proteger datos y códigos claves que podrían usarse de forma incorrecta, afectando a la experiencia del usuario. Cada permiso se define con una etiqueta única. Ejemplo: `android.permission.CALL_EMERGENCY_NUMBERS`

persistent=["true" | "**false**"] :heavy_minus_sign: Si la aplicación debe seguir ejecutándose o no en todo momento. El modo persistencia está destinado sobretodo para ciertas aplicaciones del sistema.

process="string" :heavy_minus_sign: Nombre de un proceso donde todos los componentes de la aplicación deberían correr. Cada componente puede sobreescribir este valor. Si este nombre asignado comienza con `(:)`, se crea con un nuevo proceso, privado para la aplicación cuando es necesario.

restoreAnyVersion=["**true**" | "false"] :heavy_minus_sign: Indica si la aplicación está preparada para intentar restaurar datos. Inclusos si un backup ha sido restaurado por una nueva versión de la aplicación entonces se instalará en el dispositivo. Si se pone true, permitirá al backup manager intentar restaurar cuando una versión es incompatible. Usar con cuidado.

requiredAccountType="string" :heavy_minus_sign: Especifica el tipo de cuenta requerida por la aplicación para funcionar. El valor de este atributo debe corresponder al autenticador de cuents usado por tu app (`AuthenticatorDescription`). Por ejemplo `com.google`

resizeableActivity=["true" | "false"] :heavy_minus_sign: Especifica si la app soporta multi-ventana, puedes definirlo en `<activity>` o en `<application>`

restrictedAccountType="string" :heavy_minus_sign: Especifica el tipo de cuenta requerido por la app, e indica los perfiles restringidos que permiten el acceso a dichas cuentas que pertenecen al usuario. Si tu app requiere una cuenta y perfiles restringidos pueden acceder al usuario principal y el valor de este atributo debe ser el mismo que con el tipo de autenticador de cuenta usado.

supportsRtl=["true" | "**false**"] :heavy_minus_sign: Declara si la aplicación soporta derecha-a-izquierda (RTL) layouts.

taskAffinity="string" :heavy_minus_sign: Define la afinidad que se aplica a todas las actividades dentro de la aplicación, excepto aquellas que establecen una diferente con sus propios atributos de afinidad.  Por defecto, todas las activities dentro de una app comparten la misma afinidad. El nombre es el mismo que el nombre del package  definido en `<manifest>`.

testOnly=["true" | "false"] :heavy_minus_sign: Indica si la app es solo para testeo. No se puede publicar en Google Play. Android Studio lo añade automaticamente al probarlo.

theme="resource or theme" :heavy_minus_sign: Referencia a una fuente de estilo definida por un tema por defecto para todas las activities de la aplicación. Cada activity puede tener uno propio. 

uiOptions=["**none**" | "splitActionBarWhenNarrow"] :heavy_minus_sign: Opciones extra para la UI de las activities. `splitActionBarWhenNarrow` Añade una barra abajo, al final de la pantalla para enseñar items de acción. 

usesCleartextTraffic=["**true**" | "false"] :heavy_minus_sign: Indica si la app intenta usar trádico de red, como el protocolo HTTP. Si se define como falso, los componentes rechazarán las request de usar el tráfico cleartext.  [Ver más](https://developer.android.com/guide/topics/manifest/application-element.html).

vmSafeMode=["true" | "**false**"] > :heavy_minus_sign: Indica si la app necesita que la máquina virtual funcione en modo seguro. Por defecto, falso.

####  Activity

Estructura: 

```xml
<activity>
	<intent-filter android:icon="drawable resource"
                   android:label="string resource"
                   android:priority="integer">
      <action android:name="string"/>
      <category android:name="string"/> <!-- Nombre de la categoría del intent-filter -->
      <data></data>
  </intent-filter>
<meta-data android:name="string"
           android:resource="resource specification"
           android:value="string"/>
</activity>
```

Puede contener: `<intent-filter>`, `<meta-data>`. Un ejemplo de todos sus atributos:

```xml
<activity android:allowEmbedded=["true" | "false"]
          android:allowTaskReparenting=["true" | "false"]
          android:alwaysRetainTaskState=["true" | "false"]
          android:autoRemoveFromRecents=["true" | "false"]
          android:banner="drawable resource"
          android:clearTaskOnLaunch=["true" | "false"]
          android:configChanges=["mcc", "mnc", "locale",
                                     "touchscreen", "keyboard", "keyboardHidden",
                                     "navigation", "screenLayout", "fontScale",
                                     "uiMode", "orientation", "screenSize",
                                     "smallestScreenSize"]
          android:documentLaunchMode=["intoExisting" | "always" |
                                      "none" | "never"]
          android:enabled=["true" | "false"]
          android:excludeFromRecents=["true" | "false"]
          android:exported=["true" | "false"]
          android:finishOnTaskLaunch=["true" | "false"]
          android:hardwareAccelerated=["true" | "false"]
          android:icon="drawable resource"
          android:label="string resource"
          android:launchMode=["standard"|"singleTop"|"singleTask"|"singleInstance"]
          android:maxRecents="integer"
          android:multiprocess=["true" | "false"]
          android:name="string"
          android:noHistory=["true" | "false"]  
          android:parentActivityName="string" 
          android:permission="string"
          android:process="string"
          android:relinquishTaskIdentity=["true" | "false"]
          android:resizeableActivity=["true" | "false"]
          android:screenOrientation=["unspecified" | "behind" |
                                         "landscape" | "portrait" |
                                         "reverseLandscape" | "reversePortrait" |
                                         "sensorLandscape" | "sensorPortrait" |
                                         "userLandscape" | "userPortrait" |
                                         "sensor" | "fullSensor" | "nosensor" |
                                         "user" | "fullUser" | "locked"]
          android:stateNotNeeded=["true" | "false"]
          android:supportsPictureInPicture=["true" | "false"]
          android:taskAffinity="string"
          android:theme="resource or theme"
          android:uiOptions=["none" | "splitActionBarWhenNarrow"]
          android:windowSoftInputMode=["stateUnspecified",
                                       "stateUnchanged", "stateHidden",
                                       "stateAlwaysHidden", "stateVisible",
                                       "stateAlwaysVisible", "adjustUnspecified",
                                        "adjustResize", "adjustPan"] >   
</activity>
```

allowEmbedded=["true" | "**false**"] :heavy_minus_sign: Indica que la actividad se puede iniciar como un campo secundario incorporado de otra actividad. 

alwaysRetainTaskState=["true" | "**false**"] :heavy_minus_sign: Define si el sistema siempre conservará el estado de la tarea donde se encuentra la actividad: “`true`” si es así y “`false`” si el sistema puede restablecer el estado inicial de la tarea en situaciones particulares. Este atributo solo servirá para la actividad raíz de la tarea; se ignorará en el resto de las actividades. Cuando es true, los usuarios siempre regresarán a la tarea en su último estado, sin importar cómo hayan llegado a ella.  Por ejemplo, en una aplicación, como un navegador web, con muchos estados (p. ej., varias pestañas abiertas) que los usuarios no quieren perder.

autoRemoveFromRecents=["true" | "false"] :heavy_minus_sign: Define si las tareas ejecutadas por actividades con este atributo permanecen en la [pantalla de información general](https://developer.android.com/guide/components/recents.html) hasta que se complete la última actividad de la tarea. Si es “`true`”, la tarea se quita automáticamente de la pantalla de información general.

clearTaskOnLaunch=["true" | "false"] :heavy_minus_sign: Define si todas las actividades se quitarán de la tarea, salvo la actividad raíz, cuando se vuelva a iniciar desde la pantalla de inicio (“`true`” si la tarea siempre se limpia hasta la actividad raíz y “`false`” si no es así). Cuando el valor es “`true`”, cada vez que los usuarios vuelven a iniciar la tarea, regresan a la actividad raíz independientemente de su última actividad en la tarea, y sin importar si usaron el botón *Atrás* o *Inicio* para salir. Cuando el valor es “`false`”, es posible borrar las actividades de la tarea en
algunas situaciones.

configChanges=["mcc", "mnc", "locale","touchscreen", "keyboard", "keyboardHidden", "navigation", "screenLayout", "fontScale","uiMode", "orientation", "screenSize","smallestScreenSize"] :heavy_minus_sign: Enumera los cambios de configuración que controlará la actividad.

| Valor                | Descripción                              |
| -------------------- | ---------------------------------------- |
| `mcc`                | Ha cambiado el código móvil de país (MCC) de IMSI;       se detectó una SIM y se actualizó el MCC. |
| `mnc`                | Ha cambiado el código de red móvil (MNC) de IMSI;       se detectó una SIM y se actualizó el MCC. |
| `locale`             | Ha cambiado la configuración regional; el usuario seleccionó un nuevo idioma de texto. |
| `touchscreen`        | Ha cambiado la pantalla táctil  (Normalmente, nunca debería pasar). |
| `keyboard`           | Ha cambiado el tipo de teclado; por ejemplo, el usuario conectó       un teclado externo. |
| `keyboardHidden`     | Ha cambiado la accesibilidad del teclado; por ejemplo, el       usuario expuso el teclado de hardware. |
| `navigation`         | Ha cambiado el tipo de navegación; bola de seguimiento o control de dirección.  (Normalmente, nunca debería pasar). |
| `screenLayout`       | Ha cambiado el diseño de la pantalla; posiblemente porque       se activó una pantalla distinta. |
| `fontScale`          | Ha cambiado el factor de escala de las fuentes (el usuario seleccionó       un nuevo tamaño de fuente global). |
| `uiMode`             | Ha cambiado el modo de la interfaz de usuario; puede existircuando el usuario ubica el dispositivo en un conector para autos o escritorio, o cuando cambia el modo noche. |
| `orientation`        | Ha cambiado la orientación de la pantalla; el usuario giró el dispositivo. También debes declarar la configuración de `"screenSize"`porque varía cuando un dispositivo pasa de la orientación vertical a lahorizontal. |
| `screenSize`         | Ha cambiado el tamaño de la pantalla actualmente disponible. Representa un cambio en el tamaño actualmentedisponible en función de la relación de aspecto actual. Si tu aplicación está orientada al nivel de API 12 o inferiores, tu activity siempre maneja este cambio de configuración por sí misma (este cambio de configuración no reinicia tu actividad). |
| `smallestScreenSize` | Ha cambiado el tamaño físico de la pantalla. Representa un cambio de tamaño independientemente de laorientación. Por lo tanto, solo cambiará cuando cambie el tamaño físico de la pantalla, como cuando se pasa a una pantalla externa. Sin embargo, si tu app está orientada al nivel de API 12 o inferiores, tu actividad siempre maneja este cambio de configuración por sí misma. |
| `layoutDirection`    | Ha cambiado la dirección del diseño. Por ejemplo, cuando se cambia de izquierda a derecha (LTR) o derecha a izquierda (RTL). |



documentLaunchMode=["intoExisting" | "always" | "none" | "never"] :heavy_minus_sign: Especifica la manera en que se debería agregar una nueva instancia de una actividad a una tarea cada vez que se inicia.

| Valor          | Descripción                              |
| -------------- | ---------------------------------------- |
| `intoExisting` | La actividad reutiliza la tarea existente para el documento. Usar este valor equivale a establecer  el indicador`FLAG_ACTIVITY_NEW_DOCUMENT`, *sin* establecer  el indicador`FLAG_ACTIVITY_MULTIPLE_TASK`, como se describe en  [Uso del indicador de intent para agregar una  tarea](https://developer.android.com/guide/components/recents.html#flag-new-doc). |
| `always`       | La actividad crea una tarea nueva para el documento, incluso si este ya está abierto. Es lo mismo que establecer los indicadores `FLAG_ACTIVITY_NEW_DOCUMENT` y `FLAG_ACTIVITY_MULTIPLE_TASK`. |
| `none`         | La actividad no crea una tarea nueva para la actividad. Es el valor predeterminado, que crea una tarea nueva solo cuando se establece `FLAG_ACTIVITY_NEW_TASK`.  En la pantalla de información general, la actividad recibe el mismo tratamiento que el predeterminado: se muestra una sola tarea para la app, la cual se reanuda desde la última actividad que el usuario invocó. |
| `never`        | Esta actividad no se envía a un documento nuevo, incluso si la intent contiene    `FLAG_ACTIVITY_NEW_DOCUMENT`. La configuración de este valor reemplaza el    comportamiento de los indicadores `FLAG_ACTIVITY_NEW_DOCUMENT` y `FLAG_ACTIVITY_MULTIPLE_TASK` si cualquiera de estos se fija    en la actividad, y en la pantalla de información general se muestra una sola tarea para la app, que se reanuda desde la última actividad que el usuario invocó. |

excludeFromRecents=["**true**" | "false"] :heavy_minus_sign: Define si la tarea iniciada por esta actividad debería excluirse de la lista de aplicaciones recientemente usadas.

exported=["**true**" | "false"] :heavy_minus_sign: Define si la actividad puede iniciarse a través de componentes de otras aplicaciones; “`true`” si es posible y “`false`” si no lo es. Si es “`false`”, la actividad solo se podrá iniciar a través de componentes de la misma aplicación o de aplicaciones que tengan el mismo ID de usuario.

finishOnTaskLaunch=["true" | "**false**"] :heavy_minus_sign: Define si se debe cerrar (finalizar) una instancia existente de la actividad cuando el usuario vuelve a iniciar la tarea (selecciona la tarea en la
pantalla de inicio). Será true si hay que cerrarla.

launchMode=["**standard**"|"singleTop"|"singleTask"|"singleInstance"] :heavy_minus_sign: Instrucción para el inicio de una actividad.  Existen cuatro modos que funcionan junto a los indicadores de actividad (constantes `FLAG_ACTIVITY_*`).

| Casos de uso                             | Modo de lanzamiento | ¿Varias instancias?                      | Comentarios                              |
| ---------------------------------------- | ------------------- | ---------------------------------------- | ---------------------------------------- |
| Lanzamientos convencionales para la mayoría de las actividades | “`standard`”        | Sí                                       | El sistema siempre crea una nueva instancia de la actividad en la tarea destino y direcciona la intent hacia ella. |
| “`singleTop`”                            | Condicionalmente    | Si una instancia de la actividad ya existe al comienzo de la tarea de destino,el sistema direcciona la intent hacia dicha instancia mediante un llamado a su método `onNewIntent()` en lugar de crear unanueva instancia de la actividad. |                                          |
| Lanzamientos especiales*(no se recomienda para usos generales)* | “`singleTask`”      | No                                       | El sistema crea la actividad en la raíz de una tarea nueva y direcciona la intenthacia ella. Sin embargo, si ya existe una instancia de la actividad, el sistemadirecciona la intent hacia la instancia existente mediante una llamada a su método `onNewIntent()` en lugar de crear unanueva. |
| “`singleInstance`”                       | No                  | Es igual que “`singleTask"`, con la excepción de que el sistema no lanzaotras actividades en la tarea que contiene la instancia. La actividad siempre esel único miembro de su tarea. |                                          |

maxRecents="integer" :heavy_minus_sign: Cantidad máxima de tareas que tienen la raíz en esta actividad en la [pantalla de información general](https://developer.android.com/guide/components/recents.html). Cuando se alcanza esta cantidad de entradas, el sistema quita la instancia que se usó con mayor anterioridad de la pantalla de información general. Los valores válidos van del 1 al 50 (25 en dispositivos con poca memoria). 0 no es válido.

multiprocess=["true" | "**false**"] :heavy_minus_sign: Define si se puede lanzar una instancia de la actividad en el proceso del componente que la inició (“`true`” si es posible y “`false`” si no lo es).

noHistory=["true" | "**false**"]  :heavy_minus_sign: Define si se debe quitar la actividad de la pila de actividades y finalizarla (llamar al método `finish()`) cuando el usuario salga de la actividad y no se muestre en pantalla (“`true`” si se debe finalizar y “`false`” si no se debe finalizar).

parentActivityName="string" :heavy_minus_sign: Nombre de clase del componente principal lógico de la actividad. 

process="string" :heavy_minus_sign: Nombre del proceso en el cual la actividad debe ejecutarse. Por lo general, todos los componentes de una aplicación se ejecutan en un nombre de proceso predeterminado que crea esta y no hace falta que uses este atributo. Pero si es necesario, puedes anular el nombre de proceso predeterminado con este atributo. De esta forma, podrás usar los componentes de tu app en varios procesos. Si el nombre asignado a este atributo comienza con dos puntos (“:”), se creará un proceso nuevo, privado a la aplicación, cuando sea necesario y la actividad se ejecutará en dicho proceso.

relinquishTaskIdentity=["true" | "**false**"] :heavy_minus_sign: Define si la actividad cede sus identificadores de tarea a una actividad superior en la pila de tareas. Una tarea cuya actividad raíz haya establecido este atributo en “`true`” reemplaza la intent base por la de la próxima actividad de la tarea.

screenOrientation=["unspecified" | "behind" | "landscape" | "portrait" |"reverseLandscape" | "reversePortrait" | "sensorLandscape" | "sensorPortrait" | "userLandscape" | "userPortrait" | "sensor" | "fullSensor" | "nosensor" |"user" | "fullUser" | "locked"] :heavy_minus_sign: Define la orientación en la que se mostrará la actividad en el dispositivo. El sistema ignora este atributo si la actividad se ejecuta en [modo de ventanas múltiples](https://developer.android.com/guide/topics/ui/multi-window.html).

stateNotNeeded=["true" | "false"] :heavy_minus_sign:

| `unspecified`      | Valor predeterminado.  El sistema selecciona la orientación.  La política que       usa (y en consecuencia, las elecciones que realiza en contextos específicos) puede variar de un dispositivo a otro. |
| ------------------ | ---------------------------------------- |
| `behind`           | La misma orientación de la actividad inmediatamente debajo de ella en       la pila de actividades. |
| `landscape`        | Orientación horizontal (la pantalla es más ancha que alta). |
| `portrait`         | Orientación vertical (la pantalla es más alta que ancha). |
| `reverseLandscape` | Orientación horizontal en la dirección opuesta al modo horizontal convencional.*Se agregó en nivel de API 9.* |
| `reversePortrait`  | Orientación vertical en la dirección opuesta al modo vertical convencional.*Se agregó en nivel de API 9.* |
| `sensorLandscape`  | Orientación horizontal, pero puede ser modo horizontal convencional o inverso según el sensor deldispositivo.*Se agregó en nivel de API 9.* |
| `sensorPortrait`   | Orientación vertical, pero puede ser modo vertical convencional o inverso según el sensor deldispositivo.*Se agregó en nivel de API 9.* |
| `userLandscape`    | Orientación horizontal, pero puede ser modo horizontal convencional o inverso según el sensor deldispositivo y la preferencia del usuario con respecto al sensor. Si el usuario bloqueó la rotación definida por sensor, este valor funciona igualque `landscape`. De lo contrario, se comporta igual que `sensorLandscape` |
| `userPortrait`     | Orientación vertical, pero puede ser modo vertical convencional o inverso según el sensor deldispositivo y la preferencia del usuario con respecto al sensor. Si el usuario bloqueó la rotación definida por sensor, este valor funciona igualque `portrait`. De lo contrario, se comporta igual que `sensorPortrait`. |
| `sensor`           | El sensor de orientación del dispositivo determina la orientación. La orientación de lapantalla depende de cómo el usuario sostiene el dispositivo. Sin embargo, algunos dispositivos no rotarán en las cuatro orientaciones posibles de forma predeterminada. Parapermitir la rotación en las cuatro orientaciones, usa `"fullSensor"`. |
| `fullSensor`       | El sensor de orientación del dispositivo determina la orientación para cualquiera de las 4 orientaciones. Es similar a `"sensor"`, con la excepción de que aquí se permite cualquiera de las cuatro posibles orientaciones de pantalla. |
| `nosensor`         | La orientación se determina sin hacer referencia a un sensor de orientación físico.  Se ignora elsensor; en consecuencia, la pantalla rotará independientemente del movimiento del usuario.  Salvo por estadiferencia, el sistema elige la orientación con la misma política de la configuración “`unspecified`”. |
| `user`             | La orientación que prefiere el usuario actualmente. |
| `fullUser`         | Si el usuario bloquea la rotación definida por sensor, este valor funciona igual que `user`.   De lo contrario, se comporta igual que `fullSensor` y admite cualquiera de las cuatro posibles   orientaciones de pantalla. |
| `locked`           | Bloquea la orientación en la rotación actual, sin importar la que sea. |

supportsPictureInPicture=["true" | "false"] :heavy_minus_sign: Especifica si la actividad admite pantallas [Picture-in-Picture](https://developer.android.com/training/tv/playback/picture-in-picture.jd). El sistema ignora este atributo si [`android:resizeableActivity`](https://developer.android.com/guide/topics/manifest/activity-element.html#resizeableActivity) es falso.

windowSoftInputMode=["stateUnspecified", "stateUnchanged", "stateHidden", "stateAlwaysHidden", "stateVisible", "stateAlwaysVisible", "adjustUnspecified", "adjustResize", "adjustPan"] :heavy_minus_sign:  Modo en que interactúa la ventana principal de la actividad con la ventana que contiene el teclado de software en pantalla. Influye en dos aspectos: 

- El estado del teclado de software (oculto o visible) cuando la actividad ocupa el centro de la atención del usuario.
- El ajuste de la ventana principal de la actividad (si sereduce el tamaño para hacer lugar al teclado de software o si su contenidose desplaza para hacer visible el punto de foco actual cuando el teclado de softwarecubra parte de la ventana).

| Valor                | Descripción                              |
| -------------------- | ---------------------------------------- |
| `stateUnspecified`   | No se especifica el estado del teclado de software (oculto o       visible).  El sistema elegirá un estado adecuado ousará la configuración del tema.              Esta es la configuración predeterminada para el comportamiento del teclado de software. |
| `stateUnchanged`     | El teclado de software se mantiene en su último estado visible u oculto, cuando la actividad pasa a primer plano. |
| `stateHidden`        | El teclado de software se oculta cuando el usuario elige la actividad; es decir, cuando el usuario navega explícitamente hacia la actividad en lugar de regresar a ella desde otra. |
| `stateAlwaysHidden`  | El teclado de software siempre está oculto cuando la ventana principal de la actividad tiene  foco de entrada. |
| `stateVisible`       | El teclado de software es visible cuando normalmente corresponde (cuando el usuario navega hacia la ventana principal de la actividad). |
| `stateAlwaysVisible` | El teclado de software es visible cuando el usuario elige la actividad; es decir, cuando el usuario navega explícitamente hacia la actividad en lugar de regresar a ella desde otra. |
| `adjustUnspecified`  | No se especifica si la ventana principal de la actividad cambia de tamaño       para hacer lugar al teclado de software o si los contenidos de la ventana se desplazan para que el foco actual sea visible en la pantalla. Esta es la configuración predeterminada para el comportamiento de la ventana principal. |
| `adjustResize`       | Siempre se cambia el tamaño de la ventana principal de la actividad para hacer lugar  al teclado de software en la pantalla. |
| `adjustPan`          | La ventana principal de la actividad no cambia de tamaño para hacer lugar al teclado de software.  En cambio, los contenidos de la ventana se desplazan automáticamente para que el teclado nunca obstruya el punto de foco actual       y los usuarios siempre puedan ver lo que escriben. |



#### :black_circle: Activity-Alias

#### :black_circle: Service

#### :black_circle: Reciver

#### :black_circle: Provider





