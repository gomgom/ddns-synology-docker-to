#
# It is Dockerfile for update my device IP to AWS Lightsail DNS (It's free!).
# Before use this image, please learn how to use AWS Lightsail DNS. After that,
#
# 1. Make your DNS zone with your domain. (eg. mydomain.net)
# 2. Make your A record to point your IP.
#  (eg. example.mydomain.net, It's totally OK even you want to make mydomain.net)
#
# After make domain and A record, please input this image 
# You can use the image that is already made.
# Or if you can use SSH and docker CLI, you can make your own image with this Dockerfile. 
#
# If you don't know how to use this Dockerfile, come to below Github repository.
#  https://github.com/gomgom/ddns-synology-docker-to
#
FROM amazon/aws-cli:latest
LABEL name="ddns-synology-to-aws-lightsail"
LABEL maintainer="dev@gomgom.net"
LABEL version="1.0"
LABEL build_date="2022-03-20"

# Please write your Amazon IAM account Access key and Secret Accees key.
# You needs AWS Lightsail IAM privileges below:
#   GetDomain, UpdateDomainEntry
ENV ACCESS_KEY_ID=write_your_access_key_id
ENV SECRET_ACCESS_KEY=write_your_secret_access_key

# Please write your domain name(eg. mydomain.net) and A record name(eg. example.mydomain.net)
ENV DOMAIN_NAME=mydomain.net
ENV RECORD_NAME=example.mydomain.net

# Please write update time in seconds. (Recommend seconds is 1800 = 30 minutes, no reasons.)
ENV UPDATE_TIME=write_in_seconds

RUN yum install -y jq \
  && mkdir /root/.aws \
  && echo -e "[default]\nregion=us-east-1" > /root/.aws/config \
  && echo "[default]" > /root/.aws/credentials

ENTRYPOINT echo "aws_access_key_id=$ACCESS_KEY_ID" >> /root/.aws/credentials; \
  echo "aws_secret_access_key=$SECRET_ACCESS_KEY" >> /root/.aws/credentials; \
  while [ true ]; \
  aws lightsail get-domain --domain-name=$DOMAIN_NAME | jq -r '.domain.domainEntries[] | select(.name == env.RECORD_NAME) | .id' > /root/RECORD_ID; \
  do aws lightsail update-domain-entry --domain-name=$DOMAIN_NAME \
  --domain-entry="id=$(</root/RECORD_ID),name=$RECORD_NAME,target=$(curl -silent -L http://checkip.amazonaws.com|tail -n 1),type=A"; \
  sleep $UPDATE_TIME; done;
