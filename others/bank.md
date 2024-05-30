Bank System
```ts
import * as readline from 'readline'

class Money {
  // todo: dollar & cent can be null
  private dollar: number
  private cent: number
  constructor(dollar?: number, cent?: number) {
    this.dollar = dollar ?? 0
    this.cent = cent ?? 0
  }

  toNumber(): number {
    return this.dollar + (this.cent / 100)
  }

  static toMoney(money: string): Money { 
    let dollar = 0
    let cent = 0

    const splitted = money.split(' ')
    for (let str of splitted) {
      if (str.includes('D')) {
        const num = Number(str.replace('D', ''))
        if (Number.isNaN(num)) throw new Error('Wrong input format')
        dollar = num
      }

      if (str.includes('C')) {
        const num = Number(str.replace('C', ''))
        if (Number.isNaN(num)) throw new Error('Wrong input format')
        cent = num
      }
    }

    return new Money(dollar, cent)
  }

}

class Account {
  private username: string
  private balance: number
  constructor(username: string, balance: number) {
    this.username = username
    this.balance = balance
  }

  getUsername() {
    return this.username
  }

  deposit(moneyString: string): void {
    const money = Money.toMoney(moneyString)
    this.balance += money.toNumber()
  }

  withdraw(moneyString: string): void {
    const money = Money.toMoney(moneyString)
    this.balance -= money.toNumber()
  }

  getBalance(): string {
    if (this.balance === 0) return `0D 0C`

    const dollar = Math.floor(this.balance)
    const cent = Math.round((this.balance - dollar) * 100)

    let output = ''
    if (dollar !== 0) output += `${dollar}D `
    if (cent !== 0) output += `${cent}C`
    return output
  }
}

class Bank {

  private accounts: Map<string, Account>
  constructor() {
    this.accounts = new Map()
  }

  getAccount(username: string): Account | null {
    return this.accounts.get(username) ?? null
  }

  addAccount(account: Account): void {
    this.accounts.set(account.getUsername(), account)
  }
}

function main() {
  const bank = new Bank()
  const account = new Account('farhan', 0)
  bank.addAccount(account)

  const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
  })

  showMenu(rl, account)
  }

function showMenu(rl: readline.Interface, account: Account) {
  rl.question(`
  Select an option:
  1. Credit
  2. Debit
  3. Check Balance
  4. Exit
  `, (option) => {
      switch (option) {
        case '1':
          rl.question('Enter Amount:', (amount) => {
            account.withdraw(amount)
            console.log('SUCCESSFUL!')
            showMenu(rl, account)
          })
          break
        case '2':
          rl.question('Enter Amount:', (amount) => {
            account.deposit(amount)
            console.log('DONE')
            showMenu(rl, account)
          })
          break
        case '3':
          const balance = account.getBalance()
          console.log(`Current Balance is ${balance}`)
          showMenu(rl, account)
          break
        default:
          console.log('Thank you!')
          rl.close()
          return
      }
    })
}

main()
```