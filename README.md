# 🔁 Bidirectional ClickHouse & Flat File Data Ingestion Tool

A full-stack web application that enables seamless data transfer between ClickHouse databases and CSV files in both directions.

## 📌 Project Overview

This tool provides a user-friendly interface for:
- Exporting data from ClickHouse databases to CSV files
- Importing data from CSV files into ClickHouse tables
- Previewing and selecting columns
- Handling JWT authentication for secure ClickHouse connections
- Monitoring ingestion progress and record counts

## 🚀 Features

- 🔄 **Bidirectional Data Flow**:
  - Export data from **ClickHouse → CSV**
  - Import data from **CSV → ClickHouse**
- ✅ **JWT Authentication** for ClickHouse connections
- 📂 **CSV File Upload & Download** support
- 📋 **Schema Discovery & Column Selection**:
  - View tables and columns from ClickHouse
  - Preview column headers from uploaded CSV
- 🔍 **Data Preview** before ingestion
- 📊 **Progress Indicator** and **record count display**
- 🔁 Support for **JOIN queries** between multiple ClickHouse tables
- 🚫 **Error Handling** with user-friendly messages

## 🧑‍💻 Technologies Used

### ⚙️ Backend
- **Node.js & Express**: Web server framework
- **@apla/clickhouse**: ClickHouse client for Node.js
- **jsonwebtoken**: For handling JWT tokens
- **csv-parser & fast-csv**: For reading/writing CSV files
- **multer**: For handling file uploads
- **cors & dotenv**: Utility libraries

### 💻 Frontend
- **React**: UI framework
- **axios**: For API calls
- **react-dropzone**: For file uploads
- **react-toastify**: For status messages

## 📂 Project Structure

```
clickhouse-flatfile-ingestion-tool/
├── backend/
│   ├── server.js                # Main server entry point
│   ├── config.js                # Configuration settings
│   ├── routes/                  # API routes
│   │   ├── clickhouse.routes.js # ClickHouse connections and queries
│   │   ├── csv.routes.js        # CSV upload and download
│   │   └── index.js             # Route aggregator
│   ├── controllers/             # Business logic
│   │   ├── clickhouse.controller.js
│   │   ├── csv.controller.js
│   │   └── ingestion.controller.js
│   ├── utils/                   # Utility functions
│   │   ├── csv-parser.js
│   │   ├── clickhouse-client.js
│   │   └── auth-helper.js
│   └── data/
│       └── uploads/             # Temporary storage for uploaded files
│
├── frontend/
│   ├── public/
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── src/
│   │   ├── App.js
│   │   ├── index.js
│   │   ├── components/
│   │   │   ├── ConnectionForm.jsx
│   │   │   ├── ColumnSelector.jsx
│   │   │   ├── FileUploader.jsx
│   │   │   ├── ProgressIndicator.jsx
│   │   │   └── TableViewer.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── ClickHouseToCSV.jsx
│   │   │   └── CSVToClickHouse.jsx
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── clickhouse.service.js
│   │   │   └── csv.service.js
│   │   └── styles/
│   │       ├── main.css
│   │       └── components/
│
├── testdata/                    # Sample data for testing
│   ├── uk_price_paid.csv
│   └── sample_output.csv
│
├── package.json
├── .env.example
├── .gitignore
└── docker-compose.yml          # For local ClickHouse setup
```

## 🖼️ User Interface (UI) Flow

1. **Select Source**: Choose "ClickHouse" or "Flat File"
2. **Provide Connection Details** (ClickHouse host, port, user, JWT, etc.)
3. **Load Schema**: Fetch tables or columns
4. **Select Columns**: Choose which columns to ingest
5. **Choose Target**: Where the data should go (CSV or ClickHouse)
6. **Start Ingestion**
7. **View Results**: Ingestion complete message + record count

## 🔧 Setup Instructions

### 🖥️ Prerequisites

- Node.js (v14+) and npm
- Docker (for running ClickHouse locally if needed)
- Git

### 📁 Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/v-a-dinesh/Bidirectional-ClickHouse-Flat-File-Data-Ingestion-Tool.git
   cd Bidirectional-ClickHouse-Flat-File-Data-Ingestion-Tool
   ```

2. **Backend Setup**
   ```bash
   cd .\Data-Ingestion-Tool-Server\
   npm install
   ```

3. **Create a .env file in the backend directory**
   ```
   PORT=5000
   CLICKHOUSE_DEFAULT_HOST=localhost
   CLICKHOUSE_DEFAULT_PORT=8123
   UPLOAD_DIR=./data/uploads
   ```

4. **Start the Backend Server**
   ```bash
   npm start
   # or for development with auto-restart:
   npm run dev
   ```
   Backend will run on: http://localhost:5000

5. **Frontend Setup**
   ```bash
   cd .\Data-Ingestion-Tool-Client\
   npm install
   ```

6. **Start the Frontend App**
   ```bash
   npm start
   ```
   Frontend will be accessible at: http://localhost:3000

### 🐳 Running ClickHouse Locally with Docker

```bash
# Start ClickHouse server
docker-compose up -d
```

The ClickHouse server will be available at:
- HTTP interface: http://localhost:8123
- Native interface: localhost:9000

Default credentials:
- Username: default
- Password: (empty)

## 🧪 Testing with Sample Data

The `testdata` directory contains sample CSV files for testing the application:
- `uk_price_paid.csv`: Sample dataset for importing into ClickHouse
- `sample_output.csv`: Example of exported data format

## 📝 Usage Examples

### Example 1: CSV to ClickHouse
1. Select "Flat File" as source
2. Upload CSV file
3. Preview columns and select columns to import
4. Enter ClickHouse connection details
5. Select target table or create new one
6. Start ingestion

### Example 2: ClickHouse to CSV
1. Select "ClickHouse" as source
2. Enter connection details and authenticate
3. Select table and columns to export
4. Choose CSV export options (delimiter, header, etc.)
5. Start export
6. Download the generated CSV file

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📧 Contact

For questions or support, please open an issue in the GitHub repository.