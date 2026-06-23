# AccountType

The type of account e.g. (Credit Card, Savings).

## Example Usage

```go
import (
	"github.com/MinhalAhmedKhan/yapily-go-sdk/models/components"
)

value := components.AccountTypeCashTrading

// Open enum: custom values can be created with a direct type cast
custom := components.AccountType("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `AccountTypeCashTrading`                    | CASH_TRADING                                |
| `AccountTypeCashIncome`                     | CASH_INCOME                                 |
| `AccountTypeCashPayment`                    | CASH_PAYMENT                                |
| `AccountTypeChargeCard`                     | CHARGE_CARD                                 |
| `AccountTypeCharges`                        | CHARGES                                     |
| `AccountTypeCommission`                     | COMMISSION                                  |
| `AccountTypeCreditCard`                     | CREDIT_CARD                                 |
| `AccountTypeCurrent`                        | CURRENT                                     |
| `AccountTypeEMoney`                         | E_MONEY                                     |
| `AccountTypeLimitedLiquiditySavingsAccount` | LIMITED_LIQUIDITY_SAVINGS_ACCOUNT           |
| `AccountTypeLoan`                           | LOAN                                        |
| `AccountTypeMarginalLending`                | MARGINAL_LENDING                            |
| `AccountTypeMoneyMarket`                    | MONEY_MARKET                                |
| `AccountTypeMortgage`                       | MORTGAGE                                    |
| `AccountTypeNonResidentExternal`            | NON_RESIDENT_EXTERNAL                       |
| `AccountTypeOther`                          | OTHER                                       |
| `AccountTypeOverdraft`                      | OVERDRAFT                                   |
| `AccountTypeOvernightDeposit`               | OVERNIGHT_DEPOSIT                           |
| `AccountTypePrepaidCard`                    | PREPAID_CARD                                |
| `AccountTypeSalary`                         | SALARY                                      |
| `AccountTypeSavings`                        | SAVINGS                                     |
| `AccountTypeSettlement`                     | SETTLEMENT                                  |
| `AccountTypeTax`                            | TAX                                         |
| `AccountTypeUnknown`                        | UNKNOWN                                     |