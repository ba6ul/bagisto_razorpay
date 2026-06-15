# Bagisto Razorpay Payment Gateway

A Razorpay payment gateway package for Bagisto 2.x, built for the Indian market.

## What it does

- Creates a Razorpay order on checkout and opens the payment popup
- Verifies payment signature server-side before creating the Bagisto order
- Auto-captures payment and generates invoice on success
- Redirects back to cart with error message on failure
- Configurable from Bagisto admin panel (Key ID, Secret, Test Mode, Logo)

## Requirements

- Bagisto 2.x
- PHP 8.1+
- `razorpay/razorpay` SDK

## Installation

Add to your `composer.json`:

```json
"repositories": [
    {
        "type": "path",
        "url": "packages/ba6ul/Razorpay"
    }
],
"require": {
    "ba6ul/razorpay": "*"
}
```

Then run:

```bash
composer update
php artisan optimize:clear
```

## Configuration

Go to **Admin > Configuration > Sales > Payment Methods > Razorpay** and fill in:

- **Key ID** - from your Razorpay dashboard
- **Key Secret** - from your Razorpay dashboard  
- **Test Mode** - enable for development

Get your keys at [dashboard.razorpay.com](https://dashboard.razorpay.com)

## Notes

- Amount is converted to paise automatically
- Signature verification uses `razorpay_order_id` stored in session during checkout
- Invoice is created immediately on successful payment
- Built and used in production at [Reupap](https://reupap.com)
