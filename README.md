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
### 2.1 Basics:
- Có thể tạo file inventory với rất nhiều loại format khác nhau dựa vào các plugins có. Hiện tại, có 2 kiểu formats thông dụng đó là INI và YAML.
- File inventory mặc định dạng INI sẽ nằm ở directory `/etc/ansible/` và file đó có tên là **hosts**.
- Ví dụ file inventory có định dạng INI là:
```INI
192.168.xyz.abc

[webservers]
1.1.1.1
2.2.2.2

[database]
3.3.3.3
4.4.4.4
```
- Cụm từ trong dấu ngoặc `[]` được gọi là ***group names***, nó sinh ra để gom các host có chung nhiệm vụ lại thành 1 nhóm.
- Ví dụ tương tự với file inventory có định dạng YAML là:
```yaml
all:
  hosts:
    192.168.xyz.abc
  children:
    webservers:
      hosts:
        1.1.1.1
        2.2.2.2
    database:
      hosts:
        1.1.1.1
        3.3.3.3
        4.4.4.4
```
- **Default Group**: Trong trường hợp không define bất kỳ group nào trong inventory file, Ansible sẽ mặc định tạo ra 2 groups là: `all` và `ungrouped`. Group `all` bao gồm tất cả các hosts được liệt kê trong inventory file. Còn group `ungrouped` bao gồm tất cả các hosts mà chúng không thuộc bất kỳ một group nào khác ngoài group `all`.
> Tất cả các hosts sẽ luôn luôn thuộc **tối thiểu** 2 groups (`all` và `ungrouped` hoặc `all` và các group khác) 

> **NOTE**: group `all` là bao gồm tất cả các host được liệt kê trong inventory file. Còn group `ungrouped` là bao gồm các host không nằm trong 1 group nào cả mà nó nằm độc lập. Cụ thể như ở ví dụ trên thì group `all` bao gồm: 192.168.xyz.abc, 1.1.1.1, 2.2.2.2, 3.3.3.3, 4.4.4.4; còn `ungrouped` chi có 192.168.xyz.abc 
- **Hosts in multiple groups**: Có thể đặt mỗi hosts vào nhiều hơn 1 group. Ví dụ như hosts `1.1.1.1` thuộc 2 group không kể group `all` đó là: `webservers` và `database`.
- **Grouping group**: Có thể tạo mối quan hệ cha/con giữa các groups. Groups cha được hiểu là các groups được bao các group khác - group con hoặc group của group. Ví dụ các host con được chứa trong 2 group `a_con` và `b_con`, ta tạo group `cha` chứa 2 group con ở trên.
> Để tạo quan hệ cha con giữa các group thì ở 2 dạng format sẽ khai báo khác nhau:

    - Với INI: `:children`

    - Với YAML: `children:`
### 2.2 Passing multiple inventory sources:
### 2.3 Organizing inventory in a directory:
### 2.4 Adding variables to inventory:
### 2.5 

## 3. Playbook, Play, Tasks, module:
