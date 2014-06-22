# init.rb

�v���O�C���̊�{�ݒ�y�сA�����ǉ��A���j���[�ǉ��A���W���[���ǉ��A���͍폜���o���饥��B
�p�b�`�ނ�require�������ōs�����Ƃ������B

�ȉ����������

~~~
Redmine::Plugin.register :redmine_plugin do
  name 'Redmine plugin'
  author 'Author name'
  description 'This is a plugin for Redmine.'
  version '0.0.1'
  url 'http://example.com/path/to/plugin'
  author_url 'http://example.com/about'
end

~~~

�ȉ��� `lib/redmine/plugin.rb` ���Q�l�A���p�B

## ��{�ݒ�

### Redmine�̃o�[�W�����m�F

����o�[�W�����₻��ȍ~��Ώۂɂ��Ă���ꍇ�́A
�����ݒ肵�Ă������Ƃŕۏ؂ł���o�[�W�����𖾎��ł���B

~~~
requires_redmine(arg)

# Redmine�̃o�[�W������0.7.3�ȏ�
requires_redmine :version_or_higher => '0.7.3'
requires_redmine '0.7.3'

# Redmine�̃o�[�W������0.7��
requires_redmine '0.7'

# �����Redmine�o�[�W����
requires_redmine :version => '0.7.3'              # 0.7.3 only
requires_redmine :version => '0.7'                # 0.7.x
requires_redmine :version => ['0.7.3', '0.8.0']   # 0.7.3 or 0.8.0

# Redmine�̃o�[�W�������͈͓�
requires_redmine :version => '0.7.3'..'0.9.1'     # >= 0.7.3 and <= 0.9.1
requires_redmine :version => '0.7'..'0.9'         # >= 0.7.x and <= 0.9.x
~~~

## ����

���[���ɐݒ肷�錠��

~~~
permission(name, actions, options = {})
~~~

## ���j���[��ǉ��A�폜

### �ǉ�

~~~
menu(menu, item, url, options={})

menu :project_menu, :plugin_example, { :controller => 'example', :action => 'say_hello' }, :caption => 'Sample'
~~~

:caption �ɃV���{����n���ƁA���ꉻ�����B

### �폜

�����̃��j���[�̃����N���Ăяo���R���g���[����p�����[�^��ς������ꍇ�Ɏg���B
���̏ꍇ�͍폜��ɒǉ��������`�ɂȂ�B

~~~
delete_menu_item(menu, item)

# �g�b�v���j���[����w���v�����N���폜����
delete_menu_item :top_menu, :help
# �����N���Redmine.JP����ɂ����w���v��ǉ�����
menu :top_menu, :help, 'http://redmine.jp/', {:last => true}
~~~

## ���W���[����ǉ�

~~~
project_module(name, &block)
~~~

## �����̕��ނ�ǉ�

~~~
activity_provider(*args)
~~~

## �e�L�X�g�̏�����ǉ�

~~~
wiki_format_provider(name, formatter, helper)
~~~

## ���̃v���O�C�����K�v

���̃v���O�C���̑��݂�O��Ƃ��Ă���v���O�C���ŗ��p����B

~~~
requires_redmine_plugin(plugin_name, arg)

# foo �Ƃ����v���O�C���̃o�[�W����0.7.3�ȏオ�K�v
requires_redmine_plugin :foo, :version_or_higher => '0.7.3'
requires_redmine_plugin :foo, '0.7.3'

# foo �Ƃ����v���O�C���̓���o�[�W�������K�v
requires_redmine_plugin :foo, :version => '0.7.3'              # 0.7.3 only
requires_redmine_plugin :foo, :version => ['0.7.3', '0.8.0']   # 0.7.3 or 0.8.0
~~~
