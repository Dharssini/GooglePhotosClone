# GooglePhotosClone

# Face Recognition Application

This repository contains a face recognition application using various Python libraries. The application includes a database schema, as well as the main code for processing and recognizing faces.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Database Schema](#database-schema)
- [Schema Diagram](#schema-diagram)
- [Relationships](#relationships)
- [Contributing](#contributing)
- [License](#license)


## Installation

To install the required dependencies, use the following command:

```bash
pip install -r requirements.txt
```

## Usage

To run the main application, execute the following command:

```bash
python main.py
```

## Database Schema

The SQLite database contains five tables: `t_group`, `t_picture`, `t_label`, `t_face`, and `t_face_label`. Here are the schemas for each table:

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

## Schema Diagram

![Schema Diagram](schema_diagram.png)

## Relationships

- **t_picture.group_id** references **t_group.id**
- **t_label.group_id** references **t_group.id**
- **t_face.picture_id** references **t_picture.id**
- **t_face_label.face_id** references **t_face.id**
- **t_face_label.label_id** references **t_label.id**

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes.

## License

This project is licensed under the MIT License.

## Requirements

The project requires the following Python packages, as listed in `requirements.txt`:

- numpy==1.22.3
- opencv_python_headless==4.5.5.64
- pandas==1.4.2
- Pillow==10.2.0
- pydantic==1.9.0
- scikit_learn==1.0.2
- SQLAlchemy==1.4.35
- streamlit==1.11.1
- insightface==0.6.2
- onnxruntime

## Files

### main.py
This is the main application file for the face recognition application. To run the application, execute:

```bash
python main.py
```

### requirements.txt
This file contains the list of dependencies required to run the project. Install them using:

```bash
pip install -r requirements.txt
```

## License

This project is licensed under the MIT License.
