Task 6 – Create a Strong Password and Evaluate Its Strength

📌 Objective

To understand the importance of password complexity and evaluate password strength by creating different examples, testing them with tools, and identifying best practices for stronger security.

🛠️ Approach

Created passwords of varying complexity (weak → strong).

Tested their strength using cracklib-check, entropy calculations, and online strength checkers.

Compared results and derived best practices for secure password creation.

💻 Commands Used

# Create a file with sample passwords

cat > passwords.txt <<'EOF'

hello

Hello123

H3llo@2025!

MyS3cur3#Passw0rd_2025!!

EOF

# Check strength with cracklib-check

while IFS= read -r p; do

  echo -n "$p: "
  
  echo "$p" | cracklib-check

done < passwords.txt

# Generate random strong passwords

pwgen -sy 16 5 > generated.txt

# Calculate approximate entropy

python3 - <<'PY'

import math

charset = 94

with open('passwords.txt') as f:

    for pw in f:
        pw = pw.strip()
        if not pw: continue
        entropy = len(pw) * math.log2(charset)
        print(f"{pw:30} len={len(pw):2}  entropy≈{entropy:.2f} bits")
PY

✅ Conclusion

This task demonstrated how password length and complexity directly affect strength and resistance against attacks. By testing weak and strong examples, we learned that long, random, and mixed-character passwords provide the best security, making them harder to crack with brute-force or dictionary attacks.
