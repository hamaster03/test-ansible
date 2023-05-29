# Ansible

```yaml
#Add ansible to Path
echo "export PATH=\"`python3 -m site --user-base`/bin:\$PATH\"" >> ~/.bashrc
source ~/.bashrc

#install boto3
pip3 install boto boto3
python3 -m pip3 install boto boto3

#install ansible-lint is with pip
python3 -m pip install --user ansible-lint
```
