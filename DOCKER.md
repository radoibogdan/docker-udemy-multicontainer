## HOT reload (live update of local folder with container)
### DB container
Use a named volume DOCKERDB
/data/db is the directory where the database is the mongodb container (we can't choose it)
```docker run --name mongodb --network todo-net -v DOCKERDB:/data/db mongo ```

### Back end container
```docker run --name todo-app --rm -p 8000:8000 --network todo-net -v ${PWD}/src:/app/src todoapp ```

### Front end container
```docker run --name react-todo --rm -it -p 3000:3000 -v ${PWD}/src:/app/src frontend ```