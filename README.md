### �y�ۂ̓�MongoDB�׋���z Lightning Talk by �ѓc��
# �h�X�L�[�}���X�h���Ė{���ɂ����́H
----
## �݂Ȃ���͂ǂ��v���܂����H
- �u��������������X�L�[�}���X�ō��I�v
- �u�~�~�~�~������X�L�[�}���X��߂��Ȃ��Ƃ܂�Ȃ��I�v

## �悭���ɂ��邨�b
- �u�J�������Œ�ł��Ȃ��ꍇ�ɕ֗��v
    - RDB�ł��ł����I�Ⴆ�΁E�E�E

    ```sql
CREATE TABLE user (data TEXT);
INSERT INTO user(data) VALUES ('{"user_id":1,"screen_name":"rinrin0108","age":24}');
    ```

- �u�J�����ȂǃX�L�[�}�̕ύX���p�ɂɍs����ꍇ�ɕ֗��v
    - RDB�ł�ALTER TABLE���邾���I�Ⴆ�΁E�E�E

    ```sql
ALTER TABLE user ADD nickname TEXT;
    ```

- �u�f�[�^�𕪎U���₷���v
    - RDB�ł�

�f�p�ȋ^��
    : �Ȃɂ��A�\�`���ŃX�L�[�}��������̕����킩��₷���Ȃ��ł����H


## ACID�̊ϓ_����̕]��
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���X</td></tr>
<tr><td>atomicity�i���q���j</td><td></td><td></td></tr>
<tr><td>consistency�i��ѐ��j�F�ғ����̍���</td><td></td><td></td></tr>
<tr><td>isolation�i�Ɨ����j�F��Q�����⃁���e�i���X�̂��Ղ�</td><td></td><td></td></tr>
<tr><td>durability�i�i�����j�F�f�[�^�̔j���s�����̂����ɂ���</td><td></td><td></td></tr>
</table>



## RASIS�̊ϓ_����̕]��
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���X</td></tr>
<tr><td>Reliability�i�M�����j�F��Q�̔������ɂ���</td><td></td><td></td></tr>
<tr><td>Availability�i�p���j�F�ғ����̍���</td><td></td><td></td></tr>
<tr><td>Serviceability�i�ێ琫�j�F��Q�����⃁���e�i���X�̂��Ղ�</td><td></td><td></td></tr>
<tr><td>Integrity�i�ۑS���E���S���j�F�f�[�^�̔j���s�����̂����ɂ���</td><td></td><td></td></tr>
<tr><td>Security�i�@�����j�F�O������̐N���E�������@���R�k�̋N���ɂ���</td><td></td><td></td></tr>
</table>


## ���U�̊ϓ_����̕]��

<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���X</td></tr>
<tr><td>���U���̃R�X�g</td><td>�~</td><td>��</td></tr>
<tr><td>���ו��U</td><td>��</td><td>��</td></tr>
<tr><td>���p��</td><td>��</td><td>��</td></tr>
<tr><td>���G�Ȍ�����W�v</td><td>��</td><td>��</td></tr>
<tr><td>�g�����U�N�V����</td><td>��</td><td>��</td></tr>
</table>
