FROM chechuironman/python-oc:2.1

RUN pip install pipenv

WORKDIR /project
COPY . ./

WORKDIR /project/userapp
RUN pipenv lock -r > requirements.txt
RUN python -m pip install --upgrade -r requirements.txt -t /project/deps
WORKDIR /project

ENV PYTHONPATH=/project/deps
ENV FLASK_APP=server/__init__.py

ENV PORT=8080
EXPOSE 8080
CMD ["python", "-m", "flask", "run", "--host=0.0.0.0", "--port=8080"]