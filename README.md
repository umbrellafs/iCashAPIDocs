# iCash Gateway API Documentation
iCash is a mobile payment wallet that can be topped up from any one of our hundreds of distributors.
Its backend is also accessible via an API (Application Programming Interface) allowing 3rd parties (online stores, services...etc) to setup iCash as a payment method on their platform.

# Base URL
The base URL for all iCash endpoints is as follows:

    https://icashmerchantv2.azurewebsites.net

The API currently has 12 endpoints, each requiring certain parameters and performing a specific function as follows:
It contains the following 12 functions:    
 - [Login](#login-post)    
 - [Get Balance](#get-balance-get)    
 - [Get Statement](#get-statement-get)  
 - [Transfer Money](#transfer-money-post)  
 - [Generate Payment Code](#generate-payment-code-post)  
 - [Validate Voucher](#validate-voucher-post)  
 - [Redeem Voucher](#redeem-voucher-post)  
 - [Pay Invoice](#pay-invoice-post)  
 - [Get iCash Card Network Number](#get-icash-card-network-number-get)  
 - [Can Customer Purchase](#can-customer-purchase-post)  
 - [Show QR](#show-qr-get)  
 - [Set New PIN](#set-new-pin-post) 

## Login (POST)
### Path

    {base URL}/Token

### Headers
This function requires the following:

    {
    "Content-Type" : "application/x-www-form-urlencoded"
    }

### Parameters
This function required no parameters

### Body
This function  required the following body parameters

    {
    "UserName" : "example@website.com",
    "Password" : "P@$$W0RD",
    "grant_type" : "password"
    }

### Response

    {
    "access_token": "ixunXTrfcrfcfrcrffffffffffffffcerdcxfrcfrcfr6Tv9PTrfcrfcfrcrffffffffffffffcerdcxfrcfrcfr6Tv9PTrfcrfcfrcrffffffffffffffcerdcxfrcfrcfr6Tv9PTrfcrfcfrcrffffffffffffffcerdcxfrcfrcfr6Tv9PfXTKKp2jNl206KXoFPTJ8KLQEtP7uGPO0SkdjDl3xgxIRJgba4cOEQtxHI00RDnd4Z2KMry0IZAvqYFppgXVI2F0cfsdrsU_T2ZiLcFyAesyanB4q7dECGPnADevCImjRxBq6MtTgwdokAAbuNmG9LZ8fcfcfcAnb",
    "token_type": "bearer",
    "expires_in": 1209599,
    "userName": "Store@example.ly",
    ".expires": "Mon, 16 Dec 2019 20:30:50 GMT",
    ".issued": "Mon, 02 Dec 2019 20:30:50 GMT"
    }

## Get Balance (GET)
### Path

    {base URL}/api/ICashAccount/GetBalance

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function required the following Parameters:

    {
    "iCashCardNumber" : 7129876543
    }

### Body
This function  required no body parameters

### Response

    {
    "CurrentBalance": 10
    }

## Get Statement (GET)
### Path

    {base URL}/api/ICashAccount/GetStatement

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567,
    "From" : 2019-01-01,
    "To" : 2019-12-31,
    "NumberOfRecords" : 100
    }

### Body
This function requires no body parameters

### Response

    {
        "CurrentBalance": 19,
        "Statement": [
            {
                "debt": 0,
                "crdit": 10,
                "id": 109973,
                "transeDate": "12/2/2019 8:41:52 PM",
                "desc": "شحن رصيد ببطاقة تعبئة",
                "note": "",
                "sellerDesc": "",
                "opning": 9,
                "closing": 19,
                "opType": 15,
                "secondParty": "0",
                "secondPartyAccountId": "606"
            },
            {
                "debt": 1,
                "crdit": 0,
                "id": 109968,
                "transeDate": "12/2/2019 8:36:31 PM",
                "desc": "تحويل مالي رقم 11243 إلى  1000100550",
                "note": "",
                "sellerDesc": "Hi",
                "opning": 10,
                "closing": 9,
                "opType": -1,
                "secondParty": "1000100550",
                "secondPartyAccountId": "171"
            },
            {
                "debt": 0,
                "crdit": 10,
                "id": 109533,
                "transeDate": "12/2/2019 3:37:37 PM",
                "desc": "شحن رصيد ببطاقة تعبئة",
                "note": "",
                "sellerDesc": "",
                "opning": 0,
                "closing": 10,
                "opType": 15,
                "secondParty": "0",
                "secondPartyAccountId": "8365"
            }
        ]
    }

## Transfer Money (POST)
### Path

    {base URL}/api/ICashAccount/TransferMoney

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "ReseveriCashCardNumber" : 7127654321,
    "Amount" : 25,
    "Message" : "This is an example message"
    }

### Response

    {
    "OperationReferenceNumber": 110076,
    "DateTime": "2019-12-03T02:15:31.2588197+00:00"
    }

## Generate Payment Code (POST)
### Path

    {base URL}/api/ICashAccount/GeneratePaymentCode

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "ShopNumber" : 10,
    "Amount" : 5
    }

### Response

    {
        "PaymentCode": 857342,
        "DateTime": "2019-12-03T02:15:44.0246868+00:00"
    }

## Validate Voucher (POST)
### Path

    {base URL}/api/ICashAccount/ValidateVoucher

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "Voucher" : 75311972192799,
    "VoucherValue" : 10
    }

### Response

    {
    "SecretNo": "75311972192799",
    "Amount": 10,
    "Valid": false,
    "VoucherICashNetwork": 1,
    "ChargeDate": "2019-10-16T22:13:41"
    }

## Redeem Voucher (POST)
### Path

    {base URL}/api/ICashAccount/RedeemVoucher

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "Voucher" : 75311972192799,
    "VoucherValue" : 10
    }

### Response

    {
        "OperationReferenceNumber": 137211,
        "DateTime": "2019-12-03T02:16:53.3246711+00:00"
    }

## Pay Invoice (POST)
### Path
    {base URL}/api/ICashAccount/PayInvoice

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "CustomeriCashCardNumber" : 7127654321,
    "InvoiceTotalAmount" : 120
    "PaymentCode" : 1807676
    "Description" : "This is a demo description"
    }

## Get iCash Card Network Number (GET)
### Path

    {base URL}/api/ICashAccount/GetiCashCardNetworkNumber

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires no body parameters

### Response

    {
        "PackageNumber": 712
    }

## Can Customer Purchase (POST)
### Path

    {base URL}/api/Merchant/CanCustomerPurchase

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function requires the following body parameters:

    {
    "CustomeriCashCardNumber" : 7127654321,
    "Amount" : 120
    "GenerateInvoiceQR" : false
    }

### Reponse

    Inert Response Here

## Show QR (GET)
### Path

    {base URL}/api/Merchant/GeneratePaymentQR

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function required the following Parameters:

    {
    "Amount" : 100,
    "ShopID" : 10
    }

### Body
This function no body parameters

### Respose
The function returns a QR code for the invoice amount and shop number as a .png image

## Set New PIN (POST)
### Path

    {base URL}/api/ICashAccount/SetNewPIN

### Headers
This function requires the following headers:

    {
    "Content-Type": "application/x-www-form-urlencoded",
    "Authorization": "Bearer {accessToken}"
    }

### Parameters
This function requires the following parameters:

    {
    "iCashCardNumber" : 7121234567
    }

### Body
This function  required the following body parameters
    
    {
    "PIN" : 12345
    "ConfirmPIN" : 12345
    }

### Response
    {
    "IsOperationSuccessful": true,
    "DateTime": "2019-12-03T02:16:53.3246711+00:00"
    }
