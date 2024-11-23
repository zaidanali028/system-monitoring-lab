# System Monitoring Lab 🖥️

A Python-based system monitoring solution that tracks CPU, RAM, and Disk usage metrics and sends email alerts when thresholds are exceeded.

## Features

- Real-time monitoring of system resources
- Customizable alert thresholds
- Automated email notifications via Mailjet
- Low resource footprint
- Easy to configure and deploy

## Prerequisites

- Python 3.6+
- Mailjet account
- Linux/Unix/Windows system with admin privileges

## Installation

1. Clone this repository:
```bash
git clone https://github.com/zaidanali028/system-monitoring-lab.git
cd system-monitoring-lab
```

2. Create and activate virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
.\venv\Scripts\activate   # Windows
```

3. Install required packages:
```bash
pip install psutil mailjet_rest 
```

## Configuration

4. Environment Variables Setup Guide

This guide explains how to set up the required environment variables for secure credential management across different operating systems.

## Overview

Instead of using `.env` files, we recommend adding environment variables directly to your system for enhanced security. This approach prevents accidental exposure of sensitive credentials in configuration files.

## Required Environment Variables

The following environment variables must be configured:
- `MAIL_JET_API_KEY`: Your Mailjet API key
- `MAIL_JET_API_SECRET`: Your Mailjet API secret
- `SYSTEM_EMAIL`: Sender email address
- `ADMIN_EMAIL`: Admin recipient email address

## Setup Instructions(ENVIRONMENT VARIABLES)

### Linux/MacOS

I. Open your terminal and edit your shell configuration file:
   ```bash
   # For bash users
   nano ~/.bashrc
   
   # For zsh users
   nano ~/.zshrc
   ```

II. Add the following lines to the file:
   ```bash
   export MAIL_JET_API_KEY="your_api_key_here"
   export MAIL_JET_API_SECRET="your_api_secret_here"
   export SYSTEM_EMAIL="your_sender_email@domain.com"
   export ADMIN_EMAIL="admin_recipient@domain.com"
   ```

III. Save and reload the configuration:
   ```bash
   # For bash users
   source ~/.bashrc
   
   # For zsh users
   source ~/.zshrc
   ```

### Windows

I. Access Environment Variables:
   - Open System Properties
   - Click on "Environment Variables" in the Advanced tab

II. Add New System Variables:
   - Click "New" under System Variables
   - Add each variable separately:
     * Variable: `MAIL_JET_API_KEY` | Value: your_api_key_here
     * Variable: `MAIL_JET_API_SECRET` | Value: your_api_secret_here
     * Variable: `SYSTEM_EMAIL` | Value: your_sender_email@domain.com
     * Variable: `ADMIN_EMAIL` | Value: admin_recipient@domain.com

## Security Note

This method is preferred over `.env` files as it:
- Keeps sensitive credentials separate from your codebase
- Reduces the risk of accidentally committing credentials to version control
- Makes environment variables available system-wide
- Provides better credential management across different environments

## Verification

To verify your setup, you can echo the variables in your terminal:

```bash
# Linux/MacOS
echo $MAIL_JET_API_KEY

# Windows (Command Prompt)
echo %MAIL_JET_API_KEY%

# Windows (PowerShell)
echo $env:MAIL_JET_API_KEY
```

5. Adjust monitoring thresholds in `monitor.py` by updating the following variables:
```python
CPU_THRESHOLD = 80  # CPU usage percentage
RAM_THRESHOLD = 85  # RAM usage percentage
DISK_THRESHOLD = 90 # Disk usage percentage
```

## Usage

Run the monitoring script:
```bash
python monitor.py
```

For continuous monitoring, set up a cron job (Linux/Mac) or Task Scheduler (Windows).

### Example Cron Entry (Every 24 hours)
```bash
0 0 * * * /path/to/venv/bin/python /path/to/monitor.py
```

## Sample Alert Email

Below is an example of the system monitoring alert email:

![System Monitor Alert Email](sample.png)


## Alert Triggers

The script sends alerts when:
- CPU usage exceeds configured threshold
- RAM usage exceeds configured threshold
- Available disk space falls below threshold
- Any monitored service becomes unresponsive

## Troubleshooting

### Common Issues

1. **No Alerts Received**
   - Verify Mailjet credentials
   - Check spam folder
   - Confirm threshold settings
   - Verify internet connectivity

2. **Script Errors**
   - Ensure all environment variables are set
   - Verify Python version compatibility
   - Check system permissions

3. **High Resource Usage**
   - Adjust monitoring interval
   - Review threshold settings
   - Check for competing processes

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the [MIT](LICENSE) file for details.

## Acknowledgments

- Mailjet for email API services
- Python psutil developers
- Open source community

## Support

For support, please open an issue in the repository or contact the maintainer at zaidanali028@gmail.com.
