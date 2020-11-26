loanAmount = int(input('The loan amount is :'))
annualInterestRate = int(input('The annual interest rate is :'))
monthlyPayment = int(input('The monthly payment is:'))

startingBalance = loanAmount
payment = monthlyPayment
middleBalance = startingBalance - payment
interest = middleBalance * annualInterestRate/12/100
endingBalance = middleBalance + interest

print('''
         Starting              Middle                 Ending
Month    Balance    Payment    Balance    Interest    Balance
-------------------------------------------------------------
''')

for i in range(1,5):
    print('%8d%10.2f%10.2f%10.2f%10.2f%10.2f'%(i,
                                              startingBalance,
                                              payment,
                                              middleBalance,
                                              interest,
                                              endingBalance))
def main():
    instructions = """\nEnter one of the following:
        1 to print the contents of input transaction file
        2 to print all valid input transaction data
        3 to enter adjustment transaction
        4 to print customer report
        Q to end \n"""
    
       
while True:
    sys.stdout.write(instructions) 
    sys.stdout.flush()      
    choice = input( "Enter 1 to 4 " ) 

    if choice == "1":
        displayFile(sys.argv[1])
    elif choice == "2":
        fileIn = open(sys.argv[1], 'r')

        data=[]
            
        lines = fileIn.read().splitlines()
            
        for line in lines:
            transactionRecord = line.split('_')

        if transactionRecord[2] != 'C' and transactionRecord[2] != 'D':      
                sys.stderr.write('Invalid Transaction Code : ' + line + '\n')
            elif float(transactionRecord[3]) < 0 or float(transactionRecord[3]) > 100000 :      
                    sys.stderr.write('Invalid Transaction Amount: ' + line + '\n')
            else:    
                data.append(transactionRecord)
                
        print('%-20s%-30s%5s%10s'%('Name','Address','Txn', 'Ampunt'))
        print('='*65)
            
        for e in data:
            print('%-20s%-30s%5s%10s'%(e[0], e[1], e[2], e[3]))

        elif choice == "3":
            pass
        elif choice == "4":
            pass
        elif choice == "Q":
            break

    print ("End Simple Billing System")

if __name__ == "__main__":
    sys.argv = [sys.argv[0],'datafile1.dat']
    displayFile(sys.argv[1])
    main()
