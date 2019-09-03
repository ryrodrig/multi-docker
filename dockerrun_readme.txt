{
	"AWSEBDockerrunVersion": 2,
	"containerDefinitions": [
		{
			"name": "any-client",
			"image": "rodrr301/multi-client", // like services.client in docker-compose.yml ( similar concept name/context name of the container for other containers to refer to.
			"hostname": "client",// not essential - if marked tru , if this contianer crashes other other container would shutdown.// atleast one container must be essential.
			"essential": false
		},
		{
			"name": "any-server",
			"image": "rodrr301/multi-server",
			"hostname": "api",
			"essential": false
		},
		{
			"name": "any-worker",
			"image": "rodrr301/multi-worker",
			"hostname": "worker",
			"essential": false
		},
		{
			"name": "nginx",
			"image": "rodrr301/multi-nginx",// hostname is not necessary as we will not have any url accessed directly.
			"essential": true,
			"portMappings": [
				{
					"hostPort": 80,
					"containerPort": 80 // containter port.
				}
			]
		}
	]
}