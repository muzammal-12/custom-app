# Custom ERPNext App - My Custom App

This is a custom app developed for ERPNext to manage user roles, tax system, and other customizations for a restaurant business.

## Features

- **RBAC (Role-Based Access Control)**: 
  - Administrator, Manager, Front-of-House, Kitchen, Accountant roles.
  - Specific permissions on doc types (Sales Orders, Reservations, Invoices, etc.)
- **Tax System**:
  - NIC, NTN, and STRN numbers for Customer, Supplier, and Employee doc types.
  - Sales tax on goods, services, and further tax.
  - Integration with the eFBR IRIS platform for tax reporting (DSI and SRB).
- **HR Module**:
  - Employee NIC numbers, issue date, and expiry date.

## Installation

### Requirements

- ERPNext installed and running (version X.X.X)
- Python 3.x
- Node.js and Yarn (for front-end assets)
- Redis and MariaDB configured for ERPNext

### Steps to Install the Custom App

1. **Clone the repository**:
   
   If you haven't already cloned the repository, use the following command:
   
   ```bash
   git clone https://github.com/muzammal-12/custom-app.git
````

2. **Move the app to the apps directory**:

   Copy the `my_custom_app` directory into the `frappe-bench/apps` folder:

   ```bash
   cp -r custom-app/my_custom_app /path/to/frappe-bench/apps/
   ```

3. **Install the app**:

   After placing your custom app in the `apps` directory, install it on your site:

   ```bash
   bench --site erpsite.local install-app my_custom_app
   ```

4. **Restart Bench**:

   Finally, restart the bench server to load the new app:

   ```bash
   bench start
   ```

## Configuration

### Creating Roles and Assigning Permissions

1. Go to **Settings → Users and Permissions → Role** to create the five roles:

   * Administrator
   * Manager
   * Front-of-House
   * Kitchen
   * Accountant

2. Go to **Settings → Users and Permissions → User Permissions** to assign users to their respective roles.

3. Configure **DocType Permissions** via **Role Permissions Manager**.

   * For example:

     * **Front-of-House / POS**:

       * DocType `Point of Sale`: Read, Create, Submit, Print
       * DocType `Reservation`: Read, Create, Submit

4. **Branch-Level Restriction**: Grant permissions for specific restaurant branches by going to **Settings → Users and Permissions → User Permissions**.

### Tax Configuration

1. Add custom fields (`tax_nic`, `tax_ntn`, `tax_strn`) to the **Customer**, **Supplier**, and **Employee** DocTypes.
2. Add tax accounts to the **Company Master**:

   * Sales tax on goods
   * Sales tax on services
   * Further tax
   * Extra tax
3. Enable **DSI (Domestic Sales Invoices)** and **SRB (Sales Tax on Services)** reports for tax compliance.

## Usage

* Users with specific roles can now access only the modules they are permitted to use (e.g., Front-of-House users only see POS Orders and Reservations).
* The **Accountant** role has full access to all tax-related reports, including **Sales Invoices**, **Purchase Invoices**, and **Bank Reconciliation**.

## Troubleshooting

* If you experience any issues, check the logs located in `/frappe-bench/logs/`.
* Ensure that the tax reporting and integration with eFBR IRIS are set up correctly in the **Tax Accounting** settings.

## License

This app is licensed under the [MIT License](LICENSE).

```
