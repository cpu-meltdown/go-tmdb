# go-tmdb

[GoDoc](https://godoc.org/github.com/ryanbradynd05/go-tmdb)  --  [Code Coverage Report](http://rawgit.com/ryanbradynd05/go-tmdb/master/coverage/coverage_report.html)
=================================

A Go Wrapper for the API of [The Movie DB](http://www.themoviedb.org/). Complete [documentation](https://godoc.org/github.com/ryanbradynd05/go-tmdb) and [test suite](http://rawgit.com/ryanbradynd05/go-tmdb/master/coverage/coverage_report.html) are included.

An **api_key** is needed to use the API. Register for one at [themoviedb.org](https://www.themoviedb.org/documentation/api).

Note: This product uses the TMDb API but is not endorsed or certified by TMDb.

<img src="https://assets.tmdb.org/images/logos/var_7_0_tmdb-logo-2_Antitled.svg" alt="The Movie DB" width="200" height="200" />

## How to install

```shell
go get github.com/ryanbradynd05/go-tmdb
```

## How to use

Import the library

```go
import "github.com/ryanbradynd05/go-tmdb"
```
    
Create a var for global properties
```go
var tmdbAPI *tmdb.TMDb
```

Initialize the library using your api_key
```go
config := tmdb.Config{
		APIKey:   "YOUR_KEY",
		Proxies:  nil,
		UseProxy: false,
	}

	tmdbAPI = tmdb.Init(config)
```

Use the api methods as you want, for example:

```go
fightClubInfo, err := tmdbAPI.GetMovieInfo(550, nil)
```

To use optional parameters, pass in a map[string]string of options and values:

```go
var options = make(map[string]string)
options["language"] = "es"
spanishFightClub, err := tmdbAPI.GetMovieInfo(550, options)
```

All functions return Go structs. To return JSON, use the ToJSON function:

```go
fightClubJson, err := tmdb.ToJSON(fightClubInfo)
```

## How to test

Create a local.yml file in the root directory that mirrors the local.yml.example file. Then, either run go test to simply run the tests or run the coverage.sh file to run the tests with coverage info.

## Available methods

All themoviedb.org API v3 GET methods are included. The POST and DELETE APIs are not included yet. For examples on how to call each function, refer to that function's tests. For documentation of the TheMovieDB's API, see their [documentation](https://developers.themoviedb.org/3/).

## License 

The MIT License (MIT)
