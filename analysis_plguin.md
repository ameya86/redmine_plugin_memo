# �v���O�C���̉��

�_�E�����[�h�����v���O�C���̉�͂Ƃ��B

��{�I�ɁA�l�A�L�u�ɂ��쐬�̂��߁A
�o�O��l���R��ɂ��Ǝ㐫���܂܂�Ă��邱�Ƃ�����B

## init.rb

�ݒ�t�@�C���B

���j���[�⃂�W���[���̒ǉ��͊�{�I�� init.rb ���ōs���̂ŁA
���̃t�@�C��������Α�܂��ȑS�e���c���ł���A�͂��B

## db/migrate

�e�[�u����ǉ��A�폜�A���삷��v���O�C���̏ꍇ
db/migrate �f�B���N�g���Ƀt�@�C�������݂���̂ŁA
��܂��ɉ������Ă��邩���Ă����Ƃ悢�B

Redmine Backlogs �Ȃǂ͂��Ȃ蕡�G�Ȓ�`�ɂȂ��Ă���̂œǂނ̂͌������B
~~�́ABacklogs��migrate���o�O���Ă���
�`�P�b�g�̗�����������΂��ꂽ���Ƃ�����̂łł���Ηv�m�F���~~

## config/locales

����t�@�C���B

�����Ɋe����ɑΉ������|��f�[�^�������Ă���B
���{��� `ja.yml` �B

�����ꍇ�́A `en.yml` ������� `ja.yml` �Ƃ��ăR�s�[���A
��܂��ɖ|�󂷂�Έꉞ�͓��{��ŕ\���ł���悤�ɂȂ�͂��B

## test

�e�X�g�f�B���N�g���B
�e�X�g���쐬����Ă���Ȃ璆�g������B

�����ꍇ�͓���ۏؓx�������Ƃ������ƂɂȂ�B

�v���O�C���̃e�X�g�� rake redmine:plugins:test �Ŏ��s�ł���B
�i�vRAILS_ENV=test�ł�migrate�j

rspec�ȂǂŃe�X�g������Ă���ꍇ������H

## app/controllers/\*.rb�Aapp/models/\*.rb

�f�[�^�̕ۑ��A���H���ɃG�X�P�[�v�R��Ȃǂ����������Ă������ق����ǂ��B
SQL�C���W�F�N�V�����ȂǁB

�ۑ����Ƀ��f���� attributes �� params �����̂܂ܑ�����Ă���ꍇ��
mass assignment�Ǝ㐫�̋^�������邩�B

### �Q�l

github �� mass assignment �Ǝ㐫���˂��ꂽ��
http://blog.sorah.jp/2012/03/05/mass-assignment-vulnerability-in-github

## app/views/\*/\*

�\������ۂɃN���X�T�C�g�X�N���v�e�B���O�̐Ǝ㐫�����Ă��Ȃ��������Ă����Ɨǂ��B
