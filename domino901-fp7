FROM ubuntu:14.04
ENV dominopackagedir=domino901
#OSconfigForDomino
RUN useradd -ms /bin/bash notes
RUN usermod -aG notes notes
RUN usermod -d /local/notesdata notes
RUN sed -i '$d' /etc/security/limits.conf
RUN echo 'notes soft nofile 60000' >> /etc/security/limits.conf
RUN echo 'notes hard nofile 80000' >> /etc/security/limits.conf
RUN echo '# End of file' >> /etc/security/limits.conf

#DominoSetup
COPY sw-repo/${dominopackagedir}/ /tmp/sw-repo/
RUN /bin/bash -c "/tmp/sw-repo/install -silent -options /tmp/sw-repo/unix_response.dat"

#DominoInitScript
RUN mkdir -p /etc/sysconfig/
COPY sw-repo/initscripts/rc_domino /etc/init.d/
RUN chmod u+x /etc/init.d/rc_domino
RUN chown root.root /etc/init.d/rc_domino
COPY sw-repo/initscripts/rc_domino_script /opt/ibm/domino/
RUN chmod u+x /opt/ibm/domino/rc_domino_script
RUN chown notes.notes /opt/ibm/domino/rc_domino_script
COPY sw-repo/initscripts/rc_domino_config_notes /etc/sysconfig/

#DominoFP7Install
COPY sw-repo/domino901fp7/ /tmp/sw-repo/
ENV NUI_NOTESDIR /opt/ibm/domino/
RUN cd /tmp/sw-repo/ && bash -c "./install -script script.dat"

#ConfigDomino
COPY sw-repo/serverconfig/* /local/notesdata/
RUN su notes -c "cd /local/notesdata && /opt/ibm/domino/bin/server -silent /local/notesdata/cw01.pds"
#RUN echo "HTTPIHSEnabled=1" >> /local/notesdata/notes.ini

EXPOSE 80 1352
VOLUME ["/local/notesdata"]

# Clean up
RUN rm /tmp/* -R
