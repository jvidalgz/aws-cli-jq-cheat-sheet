
Show VpcId and CidrBlock from Vpcs containing network mask of 16 bits
```bash
 aws ec2 describe-vpcs | jq '.Vpcs[] | select(.CidrBlock | contains ("/16")) | { VpcId:.VpcId,CidrBlock:.CidrBlock }'                                            
```
Output
```bash
{                                                                                                                                                                       
  "VpcId": "vpc-example-aa",                                                                                                                                                 
  "CidrBlock": "172.31.0.0/16"                                                                                                                                                 
}                                                                                                                                                                                            
{                                                                                                                                                     
  "VpcId": "vpc-example-bb",                                                                                                                                               
  "CidrBlock": "192.168.0.0/16"                                                                                                                                                                         
}  
```

Show subnets with Tag Name equal to "DMZ"
```bash
aws ec2 describe-subnets | jq '.Subnets[] | select(any(.Tags[]?; .Key == "Name" and .Value == "DMZ"))'
```
Output
```json
{
  "Ipv6CidrBlockAssociationSet": [],
  "MapPublicIpOnLaunch": false,
  "AssignIpv6AddressOnCreation": false,
  "AvailabilityZone": "us-east-1a",
  "AvailableIpAddressCount": 251,
  "Tags": [
    {
      "Value": "DMZ",
      "Key": "Name"
    }
  ],
  "State": "available",
  "SubnetId": "subnet-example-aa",
  "CidrBlock": "192.168.1.0/24",
  "VpcId": "vpc-example-bb",
  "DefaultForAz": false
}                  
```