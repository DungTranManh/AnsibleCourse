**Trần Mạnh Dũng**

# Ansible Course

---
## 1. File có đuôi .yaml hoặc yml:
### 1.1 Data type:
### 1.2 Newline trong file yaml:
### NOTE:

>  Trong một file có đuôi .yml hoặc yaml thì có thể có rất nhiều documents, vậy nên để ngăn cách giữa các document này thì ta sử dụng dấu `---` ở đầu mỗi document.
> Ví dụ:
```yml
---
- hosts: all
  tasks:
    - name: task1
      ping: 
    - name: task2
      command:
        cmd: ifconfig -a
---
- hosts: server
  tasks: 
    - name: task3
      ping:
```

## 2. Inventory:

## 3. Playbook, Play, Tasks, module:
