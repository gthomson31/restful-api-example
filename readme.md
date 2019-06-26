# Device registry service 

## Usage 

All responses will have the form 

```json
{
	"data": "Mixed type holding the content of the response",
	"message": "Description of what happened"
}
```

Subsequent response definitions will only detail the expected value of the data field 

### List all Devices 

**Definitions**

`Get /devices`

**Response**

- `200 OK ` on Success 

```json
[
	{
		"identifier": "Floor Lamp",
		"name": "Floor Lamp",
		"device_type": "switch",
		"controller_gateway": "192.1.68.2"
	}
	{
		"identifier": "panasonic-tv",
		"name": "living-room-tv",
		"device_type": "tv",
		"controller_gateway": "192.1.68.3"
	}
]
```

### Register a new device 


**Definitions**

`POST /devices`

**Arguments**

- `"identifier":string` a globally unique identifier for this device 
- `"name" : "string"` a friendly name for this device
- `"device_type": "string"` the type of device understood by the client 
- `"controller_gateway": "string"`: the ip address of the devices controller

if the device with the given identifier already exists the exisiting device will be overwrtitten


**Response**

- `200 OK ` on Success 

```json
[
	{
		"identifier": "Floor Lamp",
		"name": "Floor Lamp",
		"device_type": "switch",
		"controller_gateway": "192.1.68.2"
	}
```

### Lookup Device Details 


`GET /device/<identifier>`

**Response**

- `404 Not Found` If device does not exist 
- `200 OK` On Success

```json
[
	{
		"identifier": "Floor Lamp",
		"name": "Floor Lamp",
		"device_type": "switch",
		"controller_gateway": "192.1.68.2"
	}
```


### Delete Device  


`DELETE /device/<identifier>`

**Response**

- `404 Not Found` If device does not exist 
- `204 No Content` On Success

