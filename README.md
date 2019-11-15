# CA_database

The class DBManager consists of the following methods:
  1. __init__(self,host,user,passwd,database):
    This method tries to connect to a DB named 'database' on the localhost with username 'user' and password 'passwd'.
    Then checks if the desired table exists. Upon having no table named 'keyStore' it creates it like that:
   ______________________________________________
   | serial_Number | name | certificate | valid |
   ______________________________________________
   
   the 'serial_Number' is the primary key with auto_increment attribute, 'name' represents the 'uid', the certificate, and finally
   the 'valid' tag which can be either 'valid' or 'revoked'.
   
  2. insert_query(self,query,q_tuple):
    This method inserts a new and valid certificate. 
    As the query is a prepared MySQL statement, the arguments are passed to it by q_tuple. 
    The q_tuple is in form of (name, certificate)
    
  3. update_query(self,query,q_tuple):
    This method updates the 'valid' tag of an entity determined by 'name' and 'certificate'. In another word, it revokes a 
    certificate of a user. The q_tuple must be in form of (name, certificate)
    
  4. get_currentState(self):
    This method returns a list [#issued certificates, #revoked certificates]
    
  5. get_revocationList(self):
    This method returns the serial number of all revoked certificates in form of a list.
    
  6. check_validCertificate(self, name):
    This method checks if a user has any valid certificates.
        if True: then it returns a list [True, [list of all valid certificates]]
        if False: again it returns a list [False, []]. Where the second argument is an empty list.
        
  7. def disconnectDB(self):
    Finally, this method disconnects our python script from the database.
