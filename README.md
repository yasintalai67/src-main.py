# src-main.py
 A professional, well-structured GitHub starter template with best practices, CI/CD, and clean code organization.
#!/usr/bin/env python3
"""
tamom-zendegi — Professional CLI Starter
"""

import argparse
import logging
from datetime import datetime
import sys

# -------------------- LOGGER SETUP --------------------
def setup_logger(verbose: bool):
    """Configure logger with optional verbose mode."""
    level = logging.DEBUG if verbose else logging.INFO
    logging.basicConfig(
        level=level,
        format="%(asctime)s | %(levelname)-8s | %(message)s",
        datefmt="%Y-%m-%d %H:%M:%S"
    )

# -------------------- COMMAND HANDLERS --------------------
def cmd_hello(args):
    logging.info(f"Hello, {args.name}!")
    print(f"👋 Welcome {args.name}! Today is {datetime.now():%A, %d %B %Y}.")

def cmd_info(args):
    print("📦 Project: tamom-zendegi")
    print("📝 Version: 1.0.0")
    print("👨‍💻 Author: Your Name")
    print("🚀 Description: A professional GitHub starter template.")

# -------------------- MAIN CLI --------------------
def main():
    parser = argparse.ArgumentParser(
        prog="tamom-zendegi",
        description="A professional CLI tool for your project."
    )
    parser.add_argument(
        "-v", "--verbose", action="store_true",
        help="Enable verbose output"
    )


        # info command
    parser_info = subparsers.add_parser("info", help="Show project info")
    parser_info.set_defaults(func=cmd_info)

    # Parse args
    args = parser.parse_args()

    if hasattr(args, "func"):
        setup_logger(args.verbose)
        args.func(args)
    else:
        parser.print_help()
        sys.exit(1)
amazing plan

