# bigER VS Code Extension - AI Agent Context Guide

## Overview
bigER is a VS Code extension for creating Entity-Relationship (ER) diagrams using a domain-specific language. This guide provides comprehensive documentation for assisting users with ER model creation, syntax, and notation support.

---

## RC_ Models Company ERD Example

### Entities and Relationships

#### 1. Customer
- **Attributes**:
  - `customer_id (PK)`
  - `name`
  - `email`
  - `status`
  - `phone_number`
  - `address`
  - `date_of_registration`

- **Relationships**:
  - 1 Customer → N Invoices

---

#### 2. Invoice
- **Attributes**:
  - `invoice_id (PK)`
  - `invoice_date`
  - `total_amount`
  - `customer_id (FK)`

- **Relationships**:
  - N Invoices ← 1 Customer
  - 1 Invoice → N InvoiceLines
  - 1 Invoice → 1 Payment
  - 1 Invoice → N Shipments

---

#### 3. InvoiceLine
- **Attributes**:
  - `invoice_id (PK, FK)`
  - `line_no (PK)`
  - `product_id (FK)`
  - `quantity`

- **Relationships**:
  - N InvoiceLines ← 1 Invoice
  - 1 InvoiceLine → 1 Product

---

#### 4. Product
- **Attributes**:
  - `product_id (PK)`
  - `name`
  - `category` (e.g., aircraft, ships, cars, decals)
  - `scale`
  - `price`
  - `stock_quantity`
  - `min_stock_quantity`
  - `manufacturer_id (FK)`

- **Relationships**:
  - 1 Product → N InvoiceLines
  - N Products → 1 Manufacturer

---

#### 5. Shipment
- **Attributes**:
  - `shipment_id (PK)`
  - `ship_date`
  - `status`
  - `invoice_id (FK)`

- **Relationships**:
  - N Shipments ← 1 Invoice
  - N Shipments → 1 PurchaseOrder

---

#### 6. PurchaseOrder
- **Attributes**:
  - `po_id (PK)`
  - `order_date`
  - `status`
  - `manufacturer_id (FK)`

- **Relationships**:
  - 1 PurchaseOrder ← N Shipments
  - N PurchaseOrders ← 1 Manufacturer

---

#### 7. Manufacturer
- **Attributes**:
  - `manufacturer_id (PK)`
  - `name`
  - `website`
  - `phone`
  - `address`

- **Relationships**:
  - 1 Manufacturer → N Products
  - 1 Manufacturer → N PurchaseOrders

---

#### 8. Payment
- **Attributes**:
  - `payment_id (PK)`
  - `invoice_id (FK)`
  - `payment_date`
  - `amount`
  - `status`

- **Relationships**:
  - 1 Payment → 1 Invoice

---

### ERD Diagram
The ERD diagram for RC_ Models Company is shown below:

![ERD Diagram](rc_models_erd.png)

---

## Best Practices

### Naming Conventions
1. **Entities**: Use singular nouns (PascalCase or snake_case)
   - ✅ `Customer`, `Invoice`, `Product`
   - ❌ `Customers`, `invoices`

2. **Relationships**: Use verbs or verb phrases
   - ✅ `Generates`, `Contains`, `Belongs_To`
   - ❌ `GeneratedBy`, `ContainsRelationship`

3. **Attributes**: Use descriptive names (snake_case common)
   - ✅ `customer_id`, `product_name`, `invoice_date`
   - ❌ `id`, `name`, `date`

### Model Organization
1. Define all entities first.
2. Then define relationships.
3. Group related entities together.
4. Use comments to document complex logic.

### Cardinality Guidelines
- Always specify cardinality when it's not 1:N.
- Use participation constraints for clarity.
- Add roles for recursive or complex relationships.
- Document business rules in comments.

### Notation Selection
- **Chen**: Educational, academic papers, conceptual design
- **Crow's Foot**: Commercial projects, database implementation
- **Bachman**: Data flow analysis, legacy system documentation
- **Default**: Quick prototyping, internal documentation

---

## Summary for AI Agents

When assisting users with bigER:

1. **Always start with proper file structure** (erdiagram keyword, optional notation).
2. **Validate entity definitions** (check for proper key/partial-key usage).
3. **Verify relationship syntax** (proper arrow usage, cardinality placement).
4. **Suggest appropriate notation** based on use case.
5. **Use roles for clarity** in recursive or complex relationships.
6. **Follow naming conventions** for professional models.
7. **Provide complete examples** when explaining concepts.
8. **Explain cardinality vs participation** clearly.
9. **Handle weak entities properly** (partial-key + weak relationship).
10. **Test syntax** against provided examples.

Remember: bigER uses `.erd` files, requires the `erdiagram` keyword, and supports four notation styles for visualization flexibility.
