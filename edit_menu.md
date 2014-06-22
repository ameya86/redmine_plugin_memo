# ���j���[����

init.rb �� Redmine::Plugin.register ���\�b�h���� menu ���\�b�h���Ăяo���Ēǉ�����B

���j���[�̎��

|���             |����|
|-----------------|----|
|:top_menu        |����̃��j���[�B�z�[���Ȃǂ�����ӏ��B�S�̂ɉe�������鍀�ڌ����B|
|:account_menu    |�E��̃��j���[�B���O�C���A���O�A�E�g�Ȃǂ�����ӏ��B���[�U�Ɋւ������ڌ����B|
|:project_menu    |�v���W�F�N�g�ŕ\������郁�j���[�B�T�v��`�P�b�g�ȂǁB�v���W�F�N�g���Ƃɕ������鍀�ڌ����B|
|:application_menu|�v���W�F�N�g���I������Ă��Ȃ����ɕ\������郁�j���[�B�f�t�H���g�ł͋�Ȃ̂ŁA�p��͕s���B|

## �ǉ�

��ʁA���j���[���A�����N��A�I�v�V�����i���o���A�ʒu�j�������Ɏw�肷��B

`lib/redmine.rb` �ŌĂяo���Ă��� `Redmine::MenuManager.map` ��
Redmine�W���̃��j���[��`�Ȃ̂ŁA�������Q�l�ɂȂ�B

~~~
menu(menu, item, url, options={})

menu :project_menu, :plugin_example, { :controller => 'example', :action => 'say_hello' }, :caption => 'Sample'
~~~

|�I�v�V����|����                                |��|
|----------|------------------------------------|---|
|:caption  |���o���B�V���{���̏ꍇ�͖|�󂳂��B|:label_issue|
|:first    |���j���[�̈�ԍ��ɒǉ�����B        |:first => true|
|:last     |���j���[�̈�ԉE�ɒǉ�����B        |:last => true|
|:before   |�w�荀�ڂ̍��ɒǉ�����B            |:before => :issues|
|:after    |�w�荀�ڂ̉E�ɒǉ�����B            |:after => :new_issue|

:last �� :before �����̃v���O�C���ȂǂƋ��������ꍇ�̋����͕s���B
�i�Ăяo�����ŏ��������H�j

## �폜

�폜���\�B�Ǝ��@�\�ɍ����ւ�����A�g�킹�����Ȃ��@�\���B���̂Ɍ����Ă��邩�H

~~~
delete_menu_item(menu, item)

# �g�b�v���j���[����w���v�����N���폜����
delete_menu_item :top_menu, :help
# �����N���Redmine.JP����ɂ����w���v��ǉ�����
menu :top_menu, :help, 'http://redmine.jp/', {:last => true}
~~~
