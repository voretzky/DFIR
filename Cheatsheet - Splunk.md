

coalesce() is an evaluation function that returns the first non-null value from a list of arguments (fields or literals) you give it. It's used with the eval command. 
          Splunk evaluates the arguments left to right and returns the value of the first one that isn't null (i.e., not empty/missing for that event). If all arguments are null, the result is null.

          Syntax

                eval new_field = coalesce(field1, field2, field3, ...)
          
          Use casea: 

                Normalizing field names when the same conceptual field is called different things across different sourcetypes or data sources. 
                For example, if some events have a src_ip field and others have source_address or clientip for the same concept, you can unify them:
        
                index=web sourcetype=access* OR sourcetype=firewall
                | eval unified_ip = coalesce(src_ip, source_address, clientip)      
          
                Fallback/default value. This ensures a field always has a value even if field value is missing, instead of showing as empty.:
                          
                eval status = coalesce(response_code, "unknown")
         
          
         
