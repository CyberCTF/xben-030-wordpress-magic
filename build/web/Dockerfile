# Upstream's Dockerfile (XBEN-030-24/wordpress/Dockerfile) with these changes:
# - the sources are copied from app/wordpress/ (the vendored benchmark folder sits in app/)
# - the build argument FLAG defaults to this lab's fixed flag, the value upstream's Makefile passes
#   (FLAG{sha256 of "XBEN-030-24"}), since the spec passes no build arguments
# - wordpress:latest is pinned to wordpress:6.5.4
FROM wordpress:6.5.4
COPY app/wordpress/ /var/www/html
ARG FLAG=FLAG{0e640864c2718bb34e01e700391986e28ecd6fbe98b4569ef4ccc4cee16a4b2c}
ENV FLAG=$FLAG
RUN echo "$FLAG" > /opt/flag.txt
RUN chown -R www-data:www-data /var/www/html

# CyberCTF per-player flag: the flag above is only the development fallback. ctf-entrypoint.sh
# puts the player's flag (CTF_FLAG_MAIN) in its place at every start, then runs the original
# entrypoint and command, repeated here unchanged.
COPY ctf-entrypoint.sh /usr/local/bin/ctf-entrypoint.sh
ENTRYPOINT ["/usr/local/bin/ctf-entrypoint.sh", "docker-entrypoint.sh"]
CMD ["apache2-foreground"]
