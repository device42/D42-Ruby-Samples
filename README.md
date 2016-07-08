#D42-Ruby-Samples

Example script for running Rubyl scripts against the Device42 API's

##Sample GET call using Ruby

	# GET example - get all devices
	
	require 'httparty'
	USERNAME = 'admin'
	PASSWORD = 'adm!nd42'
	
	base_url = "https://device42_server/"
	path = "api/1.0/devices/"
	
	auth = {:username => USERNAME, :password => PASSWORD}
	url = "#{base_url}#{path}"
	
	response = HTTParty.get(url ,
		{
			:headers => {'Content-Type' => 'application/x-www-form-urlencoded'},
			:basic_auth => auth,
			:verify => false,
		}
	)
	
	data = response.parsed_response
	puts "\nRESPONSE: ",data

##Sample POST call using Ruby

	# POST example - add new device
	
	require 'httparty'
	USERNAME = 'admin'
	PASSWORD = 'adm!nd42'
	
	base_url = "https://device42_server/"
	path = "api/1.0/devices/"
	name = "device42"
	payload = {:name => name}
	auth = {:username => USERNAME, :password => PASSWORD}
	url = "#{base_url}#{path}"
	
	response = HTTParty.post(url ,
		{
			:headers => {'Content-Type' => 'application/x-www-form-urlencoded'},
			:basic_auth => auth,
			:verify => false,
			:body => payload
		}
	)
	
	data = response.parsed_response
	puts "\nRESPONSE: ",data

##Sample DELETE call using Ruby

	# DELETE example - delete device
	
	require 'httparty'
	USERNAME = 'admin'
	PASSWORD = 'adm!nd42'
	
	base_url = "https://device42_server/"
	device_id = id_of_device_to_delete
	api_endpoint = "api/1.0/devices/"
	path = "#{api_endpoint}#{device_id}/"
	
	auth = {:username => USERNAME, :password => PASSWORD}
	url = "#{base_url}#{path}"
	
	response = HTTParty.delete(url,
		{
			:headers => {'Content-Type' => 'application/x-www-form-urlencoded'},
			:basic_auth => auth,
			:verify => false
		}
	)
	
	data = response.parsed_response
	puts "\nRESPONSE: ",data

##Sample PUT call using Ruby

	# PUT example - create a custom field
	
	require 'httparty'
	USERNAME = 'admin'
	PASSWORD = 'adm!nd42'
	
	base_url = "https://device42_server/"
	path = "api/1.0/device/custom_field/"
	
	auth = {:username => USERNAME, :password => PASSWORD}
	url = "#{base_url}#{path}"
	
	name = "device42"
	key  = "test_key"
	value = "test_value"
	
	@payload = {
		:name => name,
		:key => key,
		:value => value
		}
	
	
	payload = {:name => name}
	response = HTTParty.put(url,
		{
			:headers => {'Content-Type' => 'application/x-www-form-urlencoded'},
			:basic_auth => auth,
			:verify => false,
			:body => @payload
		}
	)
	
	data = response.parsed_response
	puts "\nRESPONSE: ",data
