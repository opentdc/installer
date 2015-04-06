# The MIT License (MIT)
#
# Copyright (c) 2015 Arbalo AG
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#
FROM opencrx:latest
MAINTAINER admin@opentdc.org
ENV PLATFORM jre-1.7
COPY files/opencrx-core-CRX.ear /root/opt/opencrx/apache-tomee-webprofile-1.7.1/apps/
RUN rm -rf $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/webapps/docs \
 && rm -rf $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/webapps/host-manager \
 && rm -rf $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/webapps/manager \
 && rm -rf $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/webapps/ROOT \
 && ls -al $HOME/opt/opencrx/apache-tomee-webprofile-1.7.1/webapps
#------------------------------------------------------------------------------
