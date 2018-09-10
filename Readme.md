
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
