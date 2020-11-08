# Data Dictionary

## Tables
[delivery](#table:-delivery), [driver](#table:-driver), [faculty](#table:-faculty), [location](#table:-location), [order](#table:-order), [person](#table:-person), [restaurant](#table:-restaurant), [staff](#table:-staff), [student](#table:-student), [vehicle](#table:-vehicle), [driver_rating](#table:-driver_rating), [restaurant_rating](#table:-restaurant_rating)

## Table: `delivery`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `delivery_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `driver_id` | INT | Not null |   |  **foreign key** to column `driver_id` on table `driver`. |
| `vehicle_id` | INT | Not null |   |  **foreign key** to column `vehicle_id` on table `vehicle`. |
| `delivery_time` | DATETIME |  | `NULL` |   |
  
### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `delivery_id` | PRIMARY |   |
| fk_delivery_driver_id | `driver_id` | INDEX |   |
| fk_delivery_vehicle_id | `vehicle_id` | INDEX |   |

## Table: `driver`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `driver_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `student_id` | INT | Not null |   |  **foreign key** to column `student_id` on table `student`. |
| `license_number` | VARCHAR(75) |  | `NULL` |   |
| `date_hired` | DATE |  | `NULL` |   |
| `rating` | FLOAT |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `driver_id` | PRIMARY |   |
| fk_D_student_id | `student_id` | INDEX |   |

## Table: `faculty`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `faculty_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `person_id` | INT | Not null |   |  **foreign key** to column `person_id` on table `person`. |
| `title` | VARCHAR(75) |  | `NULL` |   |
| `degree_college` | VARCHAR(75) |  | `NULL` |   |
| `highest_degree` | VARCHAR(75) |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `faculty_id` | PRIMARY |   |
| fk_F_person_id | `person_id` | INDEX |   |

## Table: `location`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `location_id` | INT | PRIMARY, Auto increments, Not null, Unique |   |   |
| `location_name` | VARCHAR(75) |  | `NULL` |   |
| `location_address` | VARCHAR(75) |  | `NULL` |   |
| `latitude` | VARCHAR(75) |  | `NULL` |   |
| `longitude` | VARCHAR(75) |  | `NULL` |   |
| `drop_off_point` | VARCHAR(75) |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `location_id` | PRIMARY |   |
| location_index_desc | `location_id` | UNIQUE |   |
| idx_location_location_name | `location_name` | INDEX |   |

## Table: `order`
 
### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `order_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `person_id` | INT | Not null |   |  **foreign key** to column `person_id` on table `person`. |
| `delivery_id` | INT | Not null |   |  **foreign key** to column `delivery_id` on table `delivery`. |
| `location_id` | INT | Not null |   |  **foreign key** to column `location_id` on table `location`. |
| `driver_id` | INT | Not null |   |  **foreign key** to column `driver_id` on table `driver`. |
| `restaurant_id` | INT | Not null |   |  **foreign key** to column `restaurant_id` on table `restaurant`. |
| `total_price` | FLOAT | Not null |   |   |
| `delivery_charge` | FLOAT |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `order_id` | PRIMARY |   |
| fk_O_person_id | `person_id` | INDEX |   |
| fk_O_delivery_id | `delivery_id` | INDEX |   |
| fk_O_location_id | `location_id` | INDEX |   |
| fk_O_driver_id | `driver_id` | INDEX |   |
| fk_O_restaurant_id | `restaurant_id` | INDEX |   |

## Table: `person`
 
### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `person_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `person_name` | VARCHAR(300) |  | `NULL` |   |
| `person_email` | VARCHAR(150) |  | `NULL` |   |
| `cell` | BIGINT |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `person_id` | PRIMARY |   |

## Table: `restaurant`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `restaurant_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `location` | VARCHAR(75) |  | `NULL` |   |
| `restaurant_name` | VARCHAR(75) |  | `NULL` |   |
| `schedule` | VARCHAR(75) |  | `NULL` |   |
| `website` | VARCHAR(75) |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `restaurant_id` | PRIMARY |   |

## Table: `staff`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `staff_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `person_id` | INT |  | `NULL` |  **foreign key** to column `person_id` on table `person`. |
| `position` | VARCHAR(75) |  | `NULL` |   |
| `is_admin` | VARCHAR(1) |  | `'N'` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `staff_id` | PRIMARY |   |
| fk_S_person_id | `person_id` | INDEX |   |

## Table: `student`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `student_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `person_id` | INT | Not null |   |  **foreign key** to column `person_id` on table `person`. |
| `graduation_year` | INT |  | `NULL` |   |
| `major` | VARCHAR(75) |  | `NULL` |   |
| `type` | VARCHAR(75) |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `student_id` | PRIMARY |   |
| fk_St_person_id | `person_id` | INDEX |   |

## Table: `vehicle`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `vehicle_id` | INT | PRIMARY, Auto increments, Not null |   |   |
| `vehicle_plate` | VARCHAR(75) |  | `NULL` |   |
| `model` | VARCHAR(75) |  | `NULL` |   |
| `make` | VARCHAR(75) |  | `NULL` |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `vehicle_id` | PRIMARY |   |

## Table: `driver_rating`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `person_person_id` | INT | PRIMARY, Not null |   |  **foreign key** to column `person_id` on table `person`. |
| `driver_driver_id` | INT | PRIMARY, Not null |   |  **foreign key** to column `driver_id` on table `driver`. |
| `stars` | TINYINT |  |   |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `person_person_id`, `driver_driver_id` | PRIMARY |   |
| fk_rating_person1_idx | `person_person_id` | INDEX |   |
| fk_rating_driver1_idx | `driver_driver_id` | INDEX |   |

## Table: `restaurant_rating`

### _Columns_: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `restaurant_restaurant_id` | INT | PRIMARY, Not null |   |  **foreign key** to column `restaurant_id` on table `restaurant`. |
| `person_person_id` | INT | PRIMARY, Not null |   |  **foreign key** to column `person_id` on table `person`. |
| `stars` | TINYINT |  |   |   |

### _Indices_: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| fk_restaurant_restaurant1_idx | `restaurant_restaurant_id` | INDEX |   |
| fk_restaurant_person1_idx | `person_person_id` | INDEX |   |
| PRIMARY | `restaurant_restaurant_id`, `person_person_id` | PRIMARY |   |
