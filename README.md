# pruebaPythonAnyWhere
Repositorio para aprender a subir proyectos Django en PythonAnyWhere

**Cosas consideradas**

Ya se tiene una cuenta de GitHub
Ya se tiene una cuenta de PythonAnywhere
Ya se tiene un proyecto hecho en Django subido a Github

*************************

PASOS:

Entrar en consola Bash:

1.- Crear entorno virtual

source virtualenvwrapper.sh

mkvirtualenv entorno


2.- Instalar Django en el entorno

//Para versión específica p.ej. pip install -U django==1.5.4
pip install -U django== "version"
	ó
pip install django //Para la última versión

3.- Clonar tu repositorio desde GitHub

//Por si se desea realizar cambios en un futuro desde PythonAnywhere
git clone https://"usuario":"contraseña"@github.com/"propietario"/"nombre_repo".git

//Por si solo se desea clonar

git clone https://github.com/"usuario"/"nombre_repo".git


//Salir de consola y dirigirse a pestaña "web"
4.- Agregar nueva web app
--Escoger opción Manual configuration

5.- Configurar archivo WSGI

# TURN ON THE VIRTUAL ENVIRONMENT FOR YOUR APPLICATION
activate_this = '/home/"usuario"/.virtualenvs/"nombre_entorno"/bin/activate_this.py'
execfile(activate_this, dict(__file__=activate_this))

import os
import sys

# ADD YOUR PROJECT TO THE PYTHONPATH FOR THE PYTHON INSTANCE
path = '/home/"usuario"/"carpeta_al_proyecto"/'

if path not in sys.path:
    sys.path.append(path)

os.chdir(path)

# TELL DJANGO WHERE YOUR SETTINGS MODULE IS LOCATED
os.environ['DJANGO_SETTINGS_MODULE'] = '"carpeta_que_contiene_settings".settings'

# Esto es para versiones django < 1.5
import django.core.handlers.wsgi
application = django.core.handlers.wsgi.WSGIHandler()

#Para versiones django > = 1.5
from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()

5.- Asignar ruta de nuestro entorno virtual

6.- Asignar rutas para archivos estáticos.

/static/admin		
/home/"usuario"/.virtualenvs/"nombre_entorno"/lib/python2.7/site-packages/django/contrib/admin/static/admin

/static/
/home/"usuario"/"nombre_repo"/static 
