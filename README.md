# SqlLikeOrm Android Library
Model-based sqlite helper library for Android.

## Description ##
SQL-LIKEORM is a shortener library which prevents you to repeat yourself for building sql structure for your every model. This library automatically creates sqlite table for your model classes and provides you to do your CRUD operations and running queries based on your models.

## Features ##
* Simple usage.
* Model-based CREATE,READ, DELETE.

## Todo ##
* [ ] UPDATE METHOD: For now Update methods are not available, but will be soon.
* [ ] QUERY BUILDER: Allows you to to write object-oriented SQL Queries.
* [ ] MORE TYPES: Soon will be able to store more data types in database. You can find the available data types below.

## Supported Types ##
* String
* int
* boolean
* long
* double
* Date

# Usage #

## Gradle ##
```
repositories {
	maven {
		url "https://jitpack.io"
	}
}
```

```
dependencies {
	compile 'com.github.brnskn:SqlLikeOrm:1.0'
}
```

## Using SqlLikeOrm ##

Create model class.

```java
public class Todo {
	@PrimaryKey //required
	public int id;
	public String title;
	public String content;
}
```

Set the config.

```java
List<Class> modelList = new ArrayList<>();
modelList.add(Todo.class);
//modelList.add(...);
Config.setInstance(SqlLikeBuilder.with(modelList).setDatabaseName("main.db").setDatabaseVersion(1));
```

Get database repo and insert new item.

```java
DBRepo<Todo> todoDBRepo = new DBRepo<>(this, Todo.class);
Todo newItem = new Todo();
newItem.title = "Example";
newItem.content = "Example todo item";
todoDBRepo.insert(newItem);
```

Get list.

```java
List<Todo> todoList = todoDBRepo.getList();

for(Todo todo:todoList){
	Log.d(TAG, todo.title);
	todoDBRepo.delete(todo.id);
}
```

License
--------


	Copyright 2017 Baran Sekin.

	Licensed under the Apache License, Version 2.0 (the "License");
	you may not use this file except in compliance with the License.
	You may obtain a copy of the License at

	   http://www.apache.org/licenses/LICENSE-2.0

	Unless required by applicable law or agreed to in writing, software
	distributed under the License is distributed on an "AS IS" BASIS,
	WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
	See the License for the specific language governing permissions and
	limitations under the License.
