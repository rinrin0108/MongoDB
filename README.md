### �y�ۂ̓�MongoDB�׋���z Lightning Talk by �ѓc��
# �h�X�L�[�}���X�h���Ė{���ɂ����́H
----
## �݂Ȃ���͂ǂ��v���܂����H
- �u��������������X�L�[�}���X�ō��I�v

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
        - ���������F�L�[�ƂȂ�l�ɂ���ăf�[�^�x�[�X�𕪂�����@
        - ���������F�@�\�ɂ���ăf�[�^�x�[�X�𕪂�����@

**�Ȃɂ��A�\�`���ŃX�L�[�}��������̕����킩��₷���Ȃ��H**

�Ƃ����킯�ŁA�������Ă݂��B


## ACID�̊ϓ_
�g�����U�N�V�����̊T�O�������X�L�[�}���XDB
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���XDB</td></tr>
<tr><td>atomicity�i���q���j�F�g�����U�N�V���������͑S�Ď��s����邩�A�܂��������s����Ȃ���Ԃ̂����ꂩ�ŏI���</td><td>��</td><td>�~</td></tr>
<tr><td>consistency�i��ѐ��j�F�g�����U�N�V���������̑O��Ńf�[�^�ɖ����𐶂��Ȃ�</td><td>��</td><td>�~</td></tr>
<tr><td>isolation�i�Ɨ����j�F���̃g�����U�N�V������������e������Ȃ�</td><td>��</td><td>�~</td></tr>
<tr><td>durability�i�i�����j�F��Q���������Ă��X�V���ʂ͕ێ������</td><td>��</td><td>�~</td></tr>
</table>

### �{�g���l�b�N�ɂ��Ȃ�ACID����
- RDB�ł́AACID�������m�ۂ���邪�A�f�[�^�ʂ�A�N�Z�X�p�x�̑���ɔ�����ACID�������ێ����邽�߂̃R�X�g�������ł��Ȃ��Ȃ�B�����ŁA�X�P�[���A�E�g�i���U�j���K�v�ɂȂ�B
    - RDB�ł́u���������v��u���������v���ł��邪�A���ו��U�⍂�p�����R�X�g�Ŏ������邱�Ƃ�����B�i���v���P�[�V������memcached�����������̃X�P�[���A�E�g�ɂ͌��ʂ����邪�A�X�V������e�[�u�������̃X�P�[���A�E�g�ɂ͂��܂���ʂ��Ȃ��j
        - RDB�T�[�o�̃X�P�[���A�b�v�i��^�T�[�o�ւ̍ڂ��ւ��j
        - DB�̃��v���P�[�V������V���[�h�i�p�[�e�B�V�����j�����ɂ��N���X�^�\�z
        - ���U�L���b�V���iOracle RAC��memcached�Ȃǁj�ɂ��N���X�^�\�z
- �X�L�[�}���XDB�ł́AACID�������m�ۂ��ꂸ�A�A�v���P�[�V�������ł̃t�H���[���K�v�B����ŁA�f�[�^�ʂ�A�N�Z�X�p�x�̑���ɔ����ăf�[�^�X�g�A�S�̂�������ł������̃T�[�o�ɃX�P�[���A�E�g�i���U�j�ł���B
    - �X�L�[�}���XDB�ł́A�u�������U�v����R�X�g�Ŏ����\�B

### BASE�Ƃ����l����
- �X�L�[�}���XDB�ł́ABASE�Ƃ����l������������Aconsistency�i��ѐ��j���ێ����邽�߂̃R�X�g��}���Ă���BBASE�́A�s�������������邱�Ƃ͖ő��ɂȂ��Ƃ����l�����Ɋ�Â��Ă���B
    - BA�FBasically Available
        - �p�����d������B
    - S�FSoft-state
        - ��Ԃ̌������͒ǋ����Ȃ��B
    - E�FEventually consistent
        - �ŏI�I�Ɉ�ѐ��̂��܂������΂悢�B���鎞�_�ł͍X�V����Ă��Ȃ��P�[�X������B


## RASIS�̊ϓ_�i�X�P�[���A�E�g�����ꍇ�j
<table border=1>
<tr><td></td><td>RDB</td><td>�X�L�[�}���XDB</td></tr>
<tr><td>Reliability�i�M�����j�F��Q�̔������ɂ���</td><td>��</td><td>��</td></tr>
<tr><td>Availability�i�p���j�F�ғ����̍���</td><td>��</td><td>��</td></tr>
<tr><td>Serviceability�i�ێ琫�j�F��Q�����⃁���e�i���X�̂��Ղ�</td>��<td></td><td>��</td></tr>
<tr><td>Integrity�i�ۑS���E���S���j�F�f�[�^�̔j���s�����̂����ɂ���</td><td>��</td><td>�~</td></tr>
<tr><td>Security�i�@�����j�F�O������̐N���E�������@���R�k�̋N���ɂ���</td><td>-</td><td>-</td></tr>
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



----
## �Q�l����
- ���UKey-Value�X�g�A�̖{���uBigtable�v
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/01.html
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/02.html
    - http://www.atmarkit.co.jp/fjava/rensai4/bigtable01/03.html
- CAP�藝, BASE�̂܂Ƃ߁ishmachid dot com�j
    - http://shmachid.com/database/135/
- yohei-y:weblog
    - http://yohei-y.blogspot.jp/search/label/base
