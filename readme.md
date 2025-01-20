# DevStack Compose: Lightweight PHP Development Environment

## Overview
DevStack Compose is a lightweight and versatile Docker-based development environment tailored for PHP projects. It supports both ARM (Apple Silicon M1/M2) and x86_64 (Intel) architectures, ensuring compatibility across a variety of systems. The stack includes **MariaDB**, **Nginx**, and **PHP 8.1** with **ionCube Loader** and **Xdebug**, offering everything you need for streamlined PHP development.

---

## Quick Start

### ARM (Apple M1/M2)

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/devstack-compose.git
   cd devstack-compose
   ```

2. Build the Docker containers:
   ```bash
   docker compose build
   ```

3. Start the containers:
   ```bash
   docker compose up
   ```

4. Verify the setup:
   - Navigate to [http://localhost:8016/info.php](http://localhost:8016/info.php) in your browser.
   - You should see the `phpinfo()` output confirming that PHP, ionCube Loader, and Xdebug are correctly installed.

5. Add your PHP code:
   - Copy your project files into the `./www/html/` directory.

---

### x86_64 (Intel)

1. Rename the configuration file:
   ```bash
   mv docker-compose.yml.x86_64.example docker-compose.override.yml
   ```

2. Build and start the containers:
   Follow the same steps as in the **ARM** section.

---

## Features

- **PHP 8.1:** The latest PHP version for cutting-edge development.
- **MariaDB:** A robust relational database for modern applications.
- **Nginx:** A high-performance web server for secure and efficient app delivery.
- **ionCube Loader:** For running encrypted PHP code.
- **Xdebug:** Debugging and profiling PHP applications with ease.
- **Cross-Platform Support:** Fully compatible with ARM and x86_64 architectures.

---

## File Structure

```plaintext
/devstack-compose/
├── docker-compose.yml
├── docker-compose.yml.x86_64.example
├── Dockerfile
├── www/
│   ├── html/
│   │   └── info.php   # Preconfigured for testing phpinfo()
├── logs/              # Log files for debugging
└── README.md          # Project documentation
```

---

## Customization
- Modify `docker-compose.override.yml` for environment-specific changes.
- Update the `php.ini` file to adjust PHP configurations.

---

## Contributing
We welcome contributions to improve DevStack Compose! Submit a pull request or open an issue to share your ideas or report bugs.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
