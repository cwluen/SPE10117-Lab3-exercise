def main():
        loanAmount = float(input("The loan amount is : "))
        annualInterestRate = float(input("The annual interest rate is: "))
        monthlyPayment = float(input("The monthly payment is: "))

        month = 1
        startingBalance = loanAmount
        payment = monthlyPayment
        middleBalance = loanAmount - payment
        interest = middleBalance * annualInterestRate/12/100
        endingBalance = middleBalance + interest
        
        print("\n")
        print("%25s%30s%30s"%
              ("Starting","Middle","Ending"))
        print("%10s%15s%15s%15s%15s%15s"%
              ("Month","Balance","Payment","Balance","Interest","Balance"))
        print("-"*85)
              
        while startingBalance > 0:
            print("%10d%15.2f%15.2f%15.2f%15.2f%15.2f"%
              (month,startingBalance,payment,middleBalance,interest,endingBalance))
            
            month+=1
            startingBalance = endingBalance
            
            if endingBalance > monthlyPayment:
                payment = monthlyPayment
            else: payment = endingBalance
            
            middleBalance =  startingBalance - payment
            interest = middleBalance * annualInterestRate/12/100
            endingBalance = middleBalance + interest
            
if __name__ == "__main__":
    main()
