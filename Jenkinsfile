pipeline {
  agent any
  stages {
    stage('practica') {
      steps {
        script {
          //crear variable que contiene el archivo
          def bucle = readYaml (file: 'release.yaml')
          //Determina que tipo de datos es, en este caso es un Map
          println bucle.getClass().getName()
          def nombre = "APP_JAVA-AUX"
          def version = "1.1.5"
          //Determino que archivo editar y donde esta la informacion
          def auch = 0
          //Bucle donde se compara la key con la variable nombre
          //Si coincide te cambia la version, si no coincide, pero esta en la lista te la muestra
          bucle.each{key,value->
            if (key == nombre) {
              println "La version de " + key + " antes era " + value + " ahora es " + version
              auch = 1
            } else {
              println "La version de " + key + " es " + value
            }
          }
          //Si no se encuentra en la lista añade una nueva linea con los valores
          if (auch == 0) {
            println "La version de " + nombre + " es " + version
          }
          //Sustituye los datos del value cuando coincida el nombre
          bucle.put(nombre, version)
          writeYaml file: 'release.yaml', data: bucle, overwrite: true

        }
      }
    }
  } 
}