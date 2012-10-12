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

- �u�f�[�^�𕪎U���ĕۑ�����ꍇ�ɕ֗��v
    - RDB�ł��ł����I�Ⴆ�΁E�E�E

**�Ȃɂ��A�\�`���ŃX�L�[�}��������̕����킩��₷���Ȃ��H**

�Ƃ����킯�ŁA�������Ă݂��B


## ACID�̊ϓ_
�g�����U�N�V�����̊T�O�������X�L�[�}���XDB
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���XDB</td></tr>
<tr><td>atomicity�i���q���j</td><td>��</td><td>�~</td></tr>
<tr><td>consistency�i��ѐ��j</td><td>��</td><td>�~</td></tr>
<tr><td>isolation�i�Ɨ����j</td><td>��</td><td>�~</td></tr>
<tr><td>durability�i�i�����j</td><td>��</td><td>�~</td></tr>
</table>

- RDB�ł́A�f�[�^�ʂ�A�N�Z�X�p�x�̑���ɔ����AACID�������ێ����邽�߂̃R�X�g�������ł��Ȃ��Ȃ�B�����������U���悤�B
    - RDB�ł́u���������v�i�L�[�ƂȂ�l�ɂ���ăf�[�^�x�[�X�𕪂�����@�j��u���������v�i�@�\�ɂ���ăf�[�^�x�[�X�𕪂�����@�j���ł��邪�A�^�p������B
- �X�L�[�}���XDB�ł́ABASE�Ƃ����l������������Aconsistency�i��ѐ��j���ێ����邽�߂̃R�X�g��}���Ă���BBASE�́A�s�������������邱�Ƃ͖ő��ɂȂ��Ƃ����l�����Ɋ�Â��Ă���B
    -BA�uBasically Available�v
        - �p�����d������B
    -S�uSoft-state�v
        - ��Ԃ̌������͒ǋ����Ȃ��B
    -E�uEventually consistent�v
        - �ŏI�I�Ɉ�ѐ��̂��܂������΂悢�B


## RASIS�̊ϓ_
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���XDB</td></tr>
<tr><td>Reliability�i�M�����j�F��Q�̔������ɂ���</td><td></td><td></td></tr>
<tr><td>Availability�i�p���j�F�ғ����̍���</td><td></td><td></td></tr>
<tr><td>Serviceability�i�ێ琫�j�F��Q�����⃁���e�i���X�̂��Ղ�</td><td></td><td></td></tr>
<tr><td>Integrity�i�ۑS���E���S���j�F�f�[�^�̔j���s�����̂����ɂ���</td><td></td><td></td></tr>
<tr><td>Security�i�@�����j�F�O������̐N���E�������@���R�k�̋N���ɂ���</td><td></td><td></td></tr>
</table>


## ���U�̊ϓ_

<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���XDB</td></tr>
<tr><td>���U���̃R�X�g</td><td>�~</td><td>��</td></tr>
<tr><td>���ו��U</td><td>��</td><td>��</td></tr>
<tr><td>���p��</td><td>��</td><td>��</td></tr>
<tr><td>���G�Ȍ�����W�v</td><td>��</td><td>��</td></tr>
<tr><td>�g�����U�N�V����</td><td>��</td><td>��</td></tr>
</table>
