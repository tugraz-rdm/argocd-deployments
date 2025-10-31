FROM imixs/exim4:latest

# Create non-root user 'exim' with UID/GID 1001
RUN groupadd -g 1001 exim \
 && useradd -u 1001 -g exim -r -s /bin/false exim

# Ensure Exim directories are writable
RUN mkdir -p /var/spool/exim4 /var/log/exim4 \
 && chown -R exim:exim /var/lib/exim4 /var/log/exim4 /var/spool/exim4 /etc/exim4 \
 && chmod 777 /var/spool/exim4

ADD run.sh /exim_start_non_root
RUN chown -R exim:exim /exim_start_non_root && chmod +x /exim_start_non_root

EXPOSE 8025

# Switch to non-root user
USER 1001

ENTRYPOINT ["/exim_start_non_root"]
