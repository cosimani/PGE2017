.. -*- coding: utf-8 -*-

.. _rcs_subversion:

Clase 01 - PGE 2017
===================
(Fecha: 15 de agosto)

:Autor: César Osimani
:Correo: cosimani@ubp.edu.ar
:Fecha: 15 de agosto de 2017
:Regularidad: 
	- 2 parciales 
	
	- Mini Exámenes de preguntas múltiples (se promedia para 3er nota)

	- Entrega de ejercicios que están en las clases (se promedia para 3er nota)
:Opción B: 
	- Desarrollo en Qt para Android 
	
	- Proponer un desarrollo que les interese
	
	- El proyecto reemplaza los dos parciales (no los Mini Exámenes ni ejercicios). 

	- Cumplir aproximadamente 8 horas semanales en investigación (no rinde parciales)
	
	- Se entragarán avances en cada uno de los parciales.
	
	- Es individual o grupo de dos.
:Otras opciones para obtener puntaje extra: 
	- Clonar este repositorio, mejorarlo, ampliarlo, colocar los ejercicios resueltos, etc. 
	
	- Crear un instructivo de Git, con ejemplos claros, para usar desde QtCreator.
:Opciones para proyectos: 
	- Interfaz gráfica creada a partir de un XML (o JSON). 
	
	- App que haga Croma `https://es.wikipedia.org/wiki/Croma <https://es.wikipedia.org/wiki/Croma>`_

	- Continuar con los proyectos del cuatrimestre pasado ( ViajeDirecto y Central Parking ).
:Temas principales:
	- Programación genérica y orientada a eventos
	- Sobrecarga de operadores
	- Uso de plantillas
	- Manejo de excepciones
	- Interface Humano Computadora
	- Resolver los problemas consultando documentación técnica de distintas fuentes
	- Funciones callback
	- Manejo de imágenes a nivel píxel
	- OpenGL
	- Procesamiento de imágenes
	- Creación de librerías
	

Introducción
============

**Programación Genérica**: Generalizar las funciones para que puedan ser utilizadas en varios casos.

Ventajas:
	- Reutilización de código.
	- Fácil mantenimiento de código.
	- Nos concentramos más en la lógica del sistema.

Desventajas:
	- Pérdida de interés para los amantes de la programación a bajo nivel.
	- En C++ requiere el uso de Templates y sobrecarga de operadores, que es dificultoso y poco legible.

**Programación Orientada a Eventos**: La ejecución está determinada por los sucesos que ocurran.
	- Generalmente el usuario es el que dirige la ejecución del programa.
	- Básicamente el programa queda bloqueado hasta producirse un evento.
	- Es la base de la interfaz de usuario.

*Ventajas*:
	- Mejoras en las interfaces de usuario.
	- Uso del mouse (o sea, hace tiempo estamos orientados a eventos)

*Desventajas*:
	- El hilo de ejecución se pierde de vista.
	- Es un tanto abstracto, se maneja generalmente a alto nivel.
	- Complicado para manejar los eventos a bajo nivel.
	
Plantillas
==========
- Separa la estructura del contenido.
- Permite construir un diseño predefinido
- Facilita el trabajo de realizar copias idénticas de la estructura.

- Utilización de tipos como parámetros
- Teniendo la función ordena(v). Dependerá del tipo de v para generar la función.

.. code-block::

    template<class T> void ordena(T v[])  {
    
    }

- Mecanismo que permite usar un tipo como parámetro en una clase o función.
- Clases genéricas: Es un “constructor” (o creador) de clases (no confundir con el constructor de una clase).
- Para el diseño de una clase genérica es aconsejable ir de lo particular a lo general.
- Primero diseñar y depurar una clase referido a un tipo concreto.
- Libro: El lenguaje de programación C++ de Stroustrup - 13.1 - 13.2 - 13.2.1 - 13.2.2

Clase genérica Listado
======================

- Una plantilla genera la definición de una clase. 
- A la instancia concreta de la clase generada, se la denomina especialización.

- La definición de la clase genérica Listado es la siguiente:

.. code-block::

    template <class T> class Listado  {
    private:
        int cantidad;
        int libre;
        T *v;
    
    public:
        Listado(int n=10) : cantidad(n), libre(0), v(new T[n])  {  }
        bool add(T nuevo);
        T get(int i)  {  return v[i];  }
        int length()  {  return libre;  }
    };
    
    template <class T> bool Listado<T>::add(T nuevo)  {
        if (libre < cantidad)  {
            v[libre] = nuevo;
            libre++;
            return true;
        }
        return false;
    }


- Observar que la definición de add() se realiza off-line con la sintaxis de una función genérica.

- Miembros de clases genéricas definidas off-line: Deben ser declaradas como funciones genéricas.

.. code-block::

    template <class T> bool Listado<T>::add(T nuevo)  {

        ////////////

    }

Ejercicio 1:
============

- En un archivo de cabecera definir la clase Listado con todos sus métodos off-line
- Agregar un método que inserte un elemento en la posición i desplazando los otros

.. code-block::

	bool insert(int I, T elemento)

- Agregar método que elimine todos los elementos

.. code-block::

	void clear()

- Método que elimine una cantidad x de elementos. Los últimos o los primeros según el bool.

.. code-block::
	
	void erase(int x, bool front_or_back)
	
- Método que elimine el elemento de la posición i.

.. code-block::
	
	void borrar(int i)


