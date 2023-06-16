<!-- for installation requirements.txt use below command -->
pip install -r requirements.txt

<!-- for freezing requirements use below command -->
pip freeze > requirements.txt

django-admin startproject drfecommerce

<!-- for creating project for local and production use below steps -->
1. create settings folder inside project
2. add create __init__.py file
3. move settings.py file to created settings folder
4. rename settings.py to base.py
5. create local.py and production.py
6. import from .base import * in local.py file and production.py file
7. change manage.py file like below

from drfecommerce.settings import base
def main():
    """Run administrative tasks."""
    if base.DEBUG:
        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'drfecommerce.settings.local')
    else:
        os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'drfecommerce.settings.production')

8. write ALLOWED_HOSTS = ['*'] in production.py file
9. try to run a server with debug true and false
<!-- for getting secret key use below command from python shell -->
py manage.py shell
from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())