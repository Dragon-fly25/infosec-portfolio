# IP Allow List Manager

**Automated access control list updater for a healthcare environment**

## Project Description

As a security professional working at a healthcare company, I developed this Python script to regularly maintain an **allow list** of IP addresses that are permitted to access restricted patient records.

The script automatically removes outdated or unauthorized IP addresses from `allow_list.txt` by comparing it against a `remove_list`, ensuring that only current authorized employees can access sensitive systems.

## Features

- Reads and parses an IP allow list from a text file
- Removes specified IP addresses from the allow list
- Updates the file with the revised list (one IP per line)
- Clean and well-documented code

## Technologies Used

- Python 3
- File I/O operations
- List manipulation

## How It Works

1. Opens and reads `allow_list.txt`
2. Converts the content from a string into a list
3. Removes any IP addresses that appear in the `remove_list`
4. Converts the updated list back into a string
5. Writes the revised allow list back to the file

## Sample Usage

```python
# Example remove list
remove_list = [
    "192.168.97.225",
    "192.168.158.170",
    "192.168.201.40",
    "192.168.58.57"
]