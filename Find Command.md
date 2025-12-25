find . -type f -exec file {} + | grep "text" : Finds human readable files
2>/dev/null hides error messages