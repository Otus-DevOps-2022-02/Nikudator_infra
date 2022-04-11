Nikudator Infra repository

Первое задание, подключение в одну команду к someinternalhost через bastion:

eval "$(ssh-agent)" && ssh-add ~/.ssh/id_rsa && ssh -A nikola@51.250.107.181 ssh -tt nikola@10.129.0.31

Дополнительное задание (подключение к someinternalhost через алиас):

Создаем по пути ~/.ssh/ файл config

В него прописываем:
IdentityFile /home/nikola/.ssh/id_rsa
host bastion
hostname 51.250.107.181
user nikola
forwardagent yes
host someinternalhost
hostname 10.129.0.31
user nikola
forwardagent yes
proxycommand ssh nikola@51.250.107.181 -W %h:%p




bastion_IP = 51.250.99.186
someinternalhost_IP = 10.129.0.33