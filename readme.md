# KISH

__Keep It Simple and Hard__

##

KISH a dataset annotation web application. One of the main goal is to facilitate and improve the quality of annotation of PDF documents (the current scholar publishing standard), by synchronizing PDF and structured extracted content. Annotation of PDF can go beyond bounding boxes or text selection directly on the PDF text layer, which are both imprecise and subject to multiple layout and text quality issues.

The technical approach is kept volontary very simple, with minimal dependencies and without any additional database or server to run. The tool uses an embedded SQLite dataset. It is a single page web application without server-side templating, the server only provides data via a web API, used by the application running in the browser. 

**Back-end:** python 3.7+, fastapi, fastapi-users (for secure authentication), SQLITE, sqlalchemy (that's it!)

**Front-end:** jquery, PDF.js, Bootstrap 5 

Data import/export format is JSON only. 

The Bootstrap front-end components are derived from the Sleek theme https://github.com/themefisher/sleek (MIT license).

## Requirements and install

The present tool is implemented in Python and should work correctly with Python 3.7 or higher. 

Get the github repo:

```console
git clone https://github.com/kermitt2/kish
cd kish
```
It is strongly advised to setup first a virtual environment to avoid falling into one of these gloomy python dependency marshlands - you can adjust the version of Python to be used, but be sure to be 3.7 or higher:

```console
virtualenv --system-site-packages -p python3.8 env
source env/bin/activate
```

Install the dependencies:

```console
python3 -m pip install -r requirements.txt
```

Finally install the project in editable state

```console
pip3 install -e .
```

### Start the service

The KISH Web application and API service is implemented with [FastAPI](https://fastapi.tiangolo.com) and can be started as follow on default port `8050`:  

```console
python3 kish/service.py --config my_config.yml
```

The application is then available for sign-in at http://localhost:8050/app/sign-in.html

By default, at first launch, an admin account is created with login `admin@admin.com` and password `admin`. You should set a proper admin account in the `config.yml` file:

```yaml
# default admin super-user when not already existing, admin_email must be an email and password must be kept secret 
  admin: "admin@admin.com"
  admin_password: "admin"
```

The admin has then the rights to manage users and extra fonctionalities in the web application. 

### Use the service

Once the service is started as described in the previous sections, the web service API documnetation is available at `http(s)://*host*:*port*/docs`, e.g. for instance `http://localhost:8050/docs`, based on Swagger, and `http://localhost:8050/redoc` for ReDoc documentation style. These documentations offer interactive support to support test queries. 

## License

KISH is distributed under [Apache 2.0 license](http://www.apache.org/licenses/LICENSE-2.0). 

The documentation of the project is distributed under [CC-0](https://creativecommons.org/publicdomain/zero/1.0/) license. 

If you contribute to the KISH project, you agree to share your contribution following these licenses. 

Contact: Patrice Lopez (<patrice.lopez@science-miner.com>)
