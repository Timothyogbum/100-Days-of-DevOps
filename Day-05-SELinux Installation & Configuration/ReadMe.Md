## Day 5: SELinux Installation & Configuration

### Key Learnings:
- **Target Verification:** Initially targeted `stapp01` based on a misunderstanding of the ticket; re-reading the audit requirements revealed the target was actually `stapp03`. 
- **Package Management:** Encountered dependency conflicts on CentOS Stream 9 with wildcard installs. Switched to a surgical install of `policycoreutils`, `libselinux-utils`, and `selinux-policy-targeted` to resolve.
- **Persistence:** Configured `/etc/selinux/config` to `disabled` to ensure security posture remains consistent after the scheduled maintenance reboot.

### Useful Commands:
- `dnf install -y [packages]` (Surgical install)
- `cat <<EOF > /etc/selinux/config` (Clean file initialization)