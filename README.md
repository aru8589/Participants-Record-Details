# ParticipantsRecordDetals_ICCSE-2026
## Create a file 'participantsDB.py', and execute 
import pandas as pd
#pdb:ParticipantsDataBase
#rec:Records
def insertRecords(pdb,rec):
    pdb.append(rec)
    return "1"

def allpdbDetails(pdb):
    cnt=0
    for rec in pdb:
        rec=print('Participants Details: #',cnt,' ','Name:',rec[0],' ','Payment:',rec[1],' ','Mobile No.:',rec[2],' ','email-id:',rec[3])
        cnt=cnt+1
    data = pd.DataFrame(pdb,columns=['Name', 'Payment', 'Mobile No.', 'Email-id'])
    return data
        
def getpdbDetails(pdb):
    pdb_name=input('Participants Name:')
    pstatus=input('Payment Status:')
    pcntno=input('Contact No.(w/o +:')
    pemail=input('email-id:')
    rec=(pdb_name,pstatus,pcntno,pemail)
    no=insertRecords(pdb,rec)
    print(no,'Record Inserted')

def viewMenu(pdb):
    cont="y"
    print('Choose any one of options below\n1:Participants to be recorded\n2:Participants Details\n0:Exit\n')
    while(cont=="y"):
        res=str(input('Your Choice:'))
        if(res=='1'):
            getpdbDetails(pdb)
        elif(res=='2'):
            allpdbDetails(pdb)
        elif(res=='0'):
            print('Thank you. Hope You Have A Great Experience.')
            print('Have A Good Day!! -- Team Member --\n')
            cont="n"
        else:
            print('Invalid Choice\n')


pdb=[]
viewMenu(pdb)
data = allpdbDetails(pdb)
data.to_csv('participants_database-payment.csv', mode='a',header=False,index=False)
                
