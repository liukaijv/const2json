# const2json

A Go tool to auto generate reflective maps go file and json file for your enums


## Fork
This is a fork of [const2json](https://github.com/vearutop/const2json) add features to generate a json file.


## Installation

```
go get github.com/liukaijv/const2json
```

## Usage

Having `day.go` with this contents:

```go
//go:generate const2json -type=Day

type Day int
const (
	Monday Day = iota
	Tuesday
	Wednesday
	Thursday
	Friday
	Saturday
	Sunday
)
```

After running `go generate` you will get `day_c2m_gen.go` and `day_c2m_gen.json`

the go file

```go
const _Day_name = "MondayTuesdayWednesdayThursdayFridaySaturdaySunday"

var _Day_map = map[Day]string{
	0: _Day_name[0:6],
	1: _Day_name[6:13],
	2: _Day_name[13:22],
	3: _Day_name[22:30],
	4: _Day_name[30:36],
	5: _Day_name[36:44],
	6: _Day_name[44:50],
}

func (i Day) GetMap() map[Day]string {
	return _Day_map
}
```

the json file 

```bash
{
  "Friday": 4,
  "Monday": 0,
  "Saturday": 5,
  "Sunday": 6,
  "Thursday": 3,
  "Tuesday": 1,
  "Wednesday": 2
}
```
