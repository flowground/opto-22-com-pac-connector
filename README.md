# ![LOGO](logo.png) PAC Control **flow**ground Connector

## Description

A generated **flow**ground connector for the PAC Control API (version R1.0a).

Generated from: https://api.apis.guru/v2/specs/opto22.com/pac/R1.0a/swagger.json<br/>
Generated at: 2019-05-07T17:43:29+03:00

## API Description

#### Revised: 6/15/2018

### Overview
This API provides secure access to a SNAP-PAC-R or -S series controller's variable and I/O tags. Confidentiality for API transactions is provided by HTTPS. Authentication uses HTTP Basic Authentication with an API key. An API key ID is submitted in the Basic Authentication userid field and API key value in the password field.

**For more information visit:** [developer.opto22.com](http://developer.opto22.com)

### Examples

**Read an array** of all the integer32 variables defined in the PAC's strategy.
For example, on your SNAP-PAC-R or -S series controller at IP address 1.2.3.4, you would use the URL: 

```
https://1.2.3.4/api/v1/device/strategy/vars/int32s
```
and provide appropriate authentication. The GET response will be a JSON array of name-value 
pairs such as: 
```json
[ { "nMyVeryFavoriteNumber": 22 },
  { "nWidgetsProducedToday": 22222 },
  { "DELAY_LOOP_TIME_IN_MSECS"  : 200 } ]
```
**Read the engineering units** (EU) of an analog input point configured in the PAC's strategy.
For an analog input (I/O point) named aiTemperatureInDegreesF, use 

`https://1.2.3.4/api/v1/device/strategy/ios/analogInputs/aiTemperatureInDegreesF/eu`

The GET response will be a single JSON name-value pair such as:
```json
{ "value": 72.22 }
```    

### Note on packet sizes:
When doing POSTs or GETs, the JSON payload in the body should not exceed 3k (3072 bytes).


## Authorization

Supported authorization schemes:
- Basic Authentication

## Actions

### Returns controller's type; firmware version; both mac addresses; and uptime in seconds

*Tags:* `all` `device`

### Returns the name, date, time, and CRC of the strategy currently in the controller, and the number of charts currently running. Empty strings and a 0 will be returned when there is no strategy.

*Tags:* `all` `strategy`

### Returns the name and engineering units (EU) for all analog input points in the strategy

*Tags:* `all` `ios`

### Reads the value in engineering units (EU) of the specified analog input

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of the analog input point to read

### Returns the name and engineering units (EU) for all analog output points in the strategy

*Tags:* `all` `ios`

### Reads the value in engineering units (EU) of the specified analog output

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of analog output point to read

### Sets the value of the specified analog output point

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of the analog output point to write

### Returns the name and state (true = on, false = off) of all digital input points in the strategy. If there is no strategy in the controller, or the strategy includes no digital inputs, the returned array will be empty.

*Tags:* `all` `ios`

### Returns the specified digital input point's state (true = on, false = off)

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of the digital input point to read

### Returns the name and state (true = on, false = off) of all digital output points in the strategy

*Tags:* `all` `ios`

### Returns the specified digital output point's state (true = on, false = off)

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of the digit output point to read

### Sets the value of the specified digital output point

*Tags:* `all` `ios`

#### Input Parameters
* `ioName` - _required_ - Name of the digital output point to write

### Returns an array of the name and length of all the float tables in the strategy

*Tags:* `all` `tables`

### Read table elements<br/>
> #### Examples ####<br/>
> * Read all elements in a table named ftable: https://1.2.3.4/api/v1/device/strategy/tables/floats/ftable<br/>
> * Read elements 5 and up in a table named ftable starting with index 5: https://1.2.3.4/api/v1/device/strategy/tables/floats/ftable?startIndex=5<br/>
> * Read 3 consecutive elements in a table named ftable starting with the element at index 10: https://1.2.3.4/api/v1/device/strategy/tables/floats/ftable?startIndex=10&numElements=3

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of float table to read; starting index and number of elements may be specified (defaults to all elements)
* `startIndex` - _optional_ - Index of first element to read (default is 0)
* `numElements` - _optional_ - Number of elements to read (default is number of elements in the table minus startIndex)

### Write table elements<br/>
> #### Examples ####<br/>
> * Write the values (1.5, 2.4, 3.5) to 3 consecutive elements in a table named ftable starting with the element at index 10:POST to https://1.2.3.4/api/v1/device/strategy/tables/floats/ftable?startIndex=10  with body of the POST request set to [ 1.5, 2.4, 3.5 ]

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of float table to write; starting index may be specified
* `startIndex` - _optional_ - Index of first element to write (default is 0)

### Read specified table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of float table to read
* `index` - _required_ - Index of element to read

### Write specified table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of float table to write
* `index` - _required_ - Index of element to write

### Returns an array of the name and length of all the integer32 tables in the strategy

*Tags:* `all` `tables`

### "Read a range of table elements from the specified integer32 table"<br/>
>  #### Examples ####<br/>
>  * Read all elements in a table named itable: https://1.2.3.4/api/v1/device/strategy/tables/int32s/itable<br/>
>  * Read elements 5 and up in a table named itable starting with index 5: https://1.2.3.4/api/v1/device/strategy/tables/int32s/itable?startIndex=5<br/>
>  * Read 3 consecutive elements in a table named itable starting with the element at index 10: https://1.2.3.4/api/v1/device/strategy/tables/int32s/itable?startIndex=10&numElements=3

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer32 table to read; starting index and number of elements may be specified (defaults to all elements)
* `startIndex` - _optional_ - Index of first element to read (default is 0)
* `numElements` - _optional_ - Number of elements to read (default is number of elements in the table minus startIndex)

### "Write a range of table elements"<br/>
> #### Examples ####<br/>
> * Write the values (1, 2, 3) to 3 consecutive elements in a table named itable starting with the element at index 10:POST to https://1.2.3.4/api/v1/device/strategy/tables/int32s/itable?startIndex=10  with body of the POST request set to [ 1, 2, 3 ]

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer32 table to write; starting index may be specified
* `startIndex` - _optional_ - Index of first element to write (default is 0)

### Read specified integer32 table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer32 table to read
* `index` - _required_ - Index of element to read

### Write specified integer32 table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer32 table to write
* `index` - _required_ - Index of element to write

### Returns an array of the name and length of all the integer64 tables in the strategy

*Tags:* `all` `tables`

### "Read a range of table elements from the specified integer64 table"<br/>
>  #### Examples ####<br/>
>  * Read all elements in a table named i64table: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table<br/>
>  * Read elements 5 and up in a table named i64table starting with index 5: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table?startIndex=5<br/>
>  * Read 3 consecutive elements in a table named i64table starting with the element at index 10: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table?startIndex=10&numElements=3

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer64 table to read; starting index and number of elements may be specified (defaults to all elements)
* `startIndex` - _optional_ - Index of first element to read (default is 0)
* `numElements` - _optional_ - Number of elements to read (default is number of elements in the table minus startIndex)

### "Write a range of table elements"<br/>
> #### Examples ####<br/>
> * Write the values (1, 2, 3) to 3 consecutive elements in a table named i64table starting with the element at index 10:POST to https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table?startIndex=10  with body of the POST request set to [ 1, 2, 3 ]

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer64 table to write; starting index may be specified
* `startIndex` - _optional_ - Index of first element to write; default is 0

### "Read a range of table elements from the specified integer64 table"<br/>
>  #### Examples ####<br/>
>  * Read all elements in a table named i64table: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table/_string<br/>
>  * Read elements 5 and up in a table named i64table starting with index 5: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table/_string?startIndex=5<br/>
>  * Read 3 consecutive elements in a table named i64table starting with the element at index 10: https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table/_string?startIndex=10&numElements=3

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer64 table to read; starting index and number of elements may be specified (defaults to all elements)
* `startIndex` - _optional_ - Index of first element to read (default is 0)
* `numElements` - _optional_ - Number of elements to read (default is number of elements in the table minus startIndex)

### "Write a range of table elements"<br/>
> #### Examples ####<br/>
> * Write the values (1, 2, 3) to 3 consecutive elements in a table named i64table starting with the element at index 10:POST to https://1.2.3.4/api/v1/device/strategy/tables/int64s/i64table/_string?startIndex=10  with body of the POST request set to [ "1", "2", "3" ]

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer64 table to write; starting index may be specified
* `startIndex` - _optional_ - Index of first element to write; default is 0.

### Read specified integer64 table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer64 table to read
* `index` - _required_ - Index of element to read

### Write specified integer64 table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer64 table to write
* `index` - _required_ - Index of element to write

### Read specified integer64 table element as string

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of integer64 table to read
* `index` - _required_ - Index of element to read

### Write specified integer64 table element as string

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of the integer64 table to write
* `index` - _required_ - Index of element to write

### Returns an array of the name and length of all the string tables in the strategy

*Tags:* `all` `tables`

### "Read a range of table elements from the specified string table"<br/>
>  #### Examples ####<br/>
>  * Read all elements in a table named strTable: https://1.2.3.4/api/v1/device/strategy/tables/strings/strTable<br/>
>  * Read elements 5 and up in a table named i64table starting with index 5: https://1.2.3.4/api/v1/device/strategy/tables/strings/strTable?startIndex=5<br/>
>  * Read 3 consecutive elements in a table named i64table starting with the element at index 10: https://1.2.3.4/api/v1/device/strategy/tables/strings/strTable?startIndex=10&numElements=3

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of string table to read; starting index and number of elements may be specified (defaults to all elements)
* `startIndex` - _optional_ - Index of first element to read (default is 0)
* `numElements` - _optional_ - Number of elements to read (default is number of elements in the table minus startIndex)

### "Write a range of table elements"<br/>
> #### Examples ####<br/>
> * Write the values ("first", "second", "third") to 3 consecutive elements in a table named strTable starting with the element at index 10:POST to https://1.2.3.4/api/v1/device/strategy/tables/strings/strtable?startIndex=10  with body of the POST request set to [ "first", "second", "third" ]

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of string table to write; starting index may be specified
* `startIndex` - _optional_ - Index of first element to write (default is 0)

### Read specified table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of string table to read
* `index` - _required_ - Index of element to read

### Write specified table element

*Tags:* `all` `tables`

#### Input Parameters
* `tableName` - _required_ - Name of string table to write
* `index` - _required_ - Index of element to write

### Returns the name and current value of all down timers in the strategy

*Tags:* `all` `vars`

### Returns current value of the specified down timer

*Tags:* `all` `vars`

#### Input Parameters
* `downTimerName` - _required_ - Name of the down timer variable to read

### Returns the name and value of all (single-precision) float variables in the strategy

*Tags:* `all` `vars`

### Returns value of the specified float variable

*Tags:* `all` `vars`

#### Input Parameters
* `floatName` - _required_ - Name of float variable to read

### Sets the value of a float variable

*Tags:* `all` `vars`

#### Input Parameters
* `floatName` - _required_ - Name of the float variable to write

### Returns the name and value of all integer32 variables in the strategy

*Tags:* `all` `vars`

### Returns value of the specified integer32 variable

*Tags:* `all` `vars`

#### Input Parameters
* `int32Name` - _required_ - Name of integer32 variable to read

### Sets the value of an integer32 variable

*Tags:* `all` `vars`

#### Input Parameters
* `int32Name` - _required_ - Name of integer32 variable to write

### Returns the name and value of all integer64 variables in the strategy

*Tags:* `all` `vars`

### Returns the name and value as a string of all integer64 variables in the strategy

*Tags:* `all` `vars`

### Returns value of the specified integer64 variable

*Tags:* `all` `vars`

#### Input Parameters
* `int64Name` - _required_ - Name of integer64 variable to read

### Sets the value of an integer64 variable

*Tags:* `all` `vars`

#### Input Parameters
* `int64Name` - _required_ - Name of integer64 variable to write

### Returns value of the specified integer64 variable as a string

*Tags:* `all` `vars`

#### Input Parameters
* `int64Name` - _required_ - Name of integer64 variable to read

### Sets the value of an integer64 variable as a string

*Tags:* `all` `vars`

#### Input Parameters
* `int64Name` - _required_ - Name of integer64 variable to write

### Returns the name and value of all string variables in the strategy

*Tags:* `all` `vars`

### Returns value of the specified string

*Tags:* `all` `vars`

#### Input Parameters
* `stringName` - _required_ - Name of string variable to read

### Sets the value of a string variable

*Tags:* `all` `vars`

#### Input Parameters
* `stringName` - _required_ - Name of string variable to write

### Returns the name and current value of all up timers in the strategy

*Tags:* `all` `vars`

### Returns current value of the specified up timer

*Tags:* `all` `vars`

#### Input Parameters
* `upTimerName` - _required_ - Name of the up timer variable to read

## License

**flow**ground :- Telekom iPaaS / opto-22-com-pac-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
