# GooglePhotosClone

# SQL Database Schema

This repository contains the schema for a SQLite database with five tables: `t_group`, `t_picture`, `t_label`, `t_face`, and `t_face_label`.

## Table Schemas

### t_group
| Column Name       | Data Type       | Constraints                |
|-------------------|-----------------|----------------------------|
| id                | INTEGER         | PRIMARY KEY, NOT NULL      |
| group_name        | VARCHAR(100)    |                            |
| det_threshold     | FLOAT           |                            |
| rec_threshold     | FLOAT           |                            |
| pitch_threshold   | FLOAT           |                            |
| yaw_threshold     | FLOAT           |                            |
| roll_threshold    | FLOAT           |                            |
| create_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |

### t_picture
| Column Name       | Data Type       | Constraints                |
|-------------------|-----------------|----------------------------|
| id                | INTEGER         | PRIMARY KEY, NOT NULL      |
| picture_name      | VARCHAR(100)    |                            |
| group_id          | INTEGER         |                            |
| create_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |

### t_label
| Column Name       | Data Type       | Constraints                |
|-------------------|-----------------|----------------------------|
| id                | INTEGER         | PRIMARY KEY, NOT NULL      |
| label_name        | VARCHAR(100)    |                            |
| group_id          | INTEGER         |                            |
| create_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |
| update_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |

### t_face
| Column Name       | Data Type       | Constraints                |
|-------------------|-----------------|----------------------------|
| id                | INTEGER         | PRIMARY KEY, NOT NULL      |
| face_index        | INTEGER         |                            |
| det_score         | FLOAT           |                            |
| pitch             | FLOAT           |                            |
| yaw               | FLOAT           |                            |
| roll              | FLOAT           |                            |
| bbox              | BLOB            |                            |
| embedding         | BLOB            |                            |
| picture_id        | INTEGER         |                            |
| create_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |

### t_face_label
| Column Name       | Data Type       | Constraints                |
|-------------------|-----------------|----------------------------|
| id                | INTEGER         | PRIMARY KEY, NOT NULL      |
| face_id           | INTEGER         |                            |
| label_id          | INTEGER         |                            |
| create_time       | DATETIME        | DEFAULT CURRENT_TIMESTAMP  |



## Relationships

- **t_picture.group_id** references **t_group.id**
- **t_label.group_id** references **t_group.id**
- **t_face.picture_id** references **t_picture.id**
- **t_face_label.face_id** references **t_face.id**
- **t_face_label.label_id** references **t_label.id**

## License

This project is licensed under the MIT License.
