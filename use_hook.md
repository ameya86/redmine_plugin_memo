# �p�ӂ��ꂽHook���g��

Redmine���ɗp�ӂ���Ă��鏈����ǉ�����ӏ�������AHook�ƌĂ΂�Ă���B

���\�b�h�ɕύX��������ꍇ�ɑ΂��āA���X�N�����Ȃ��̂����_�B

## Hook�̏ꏊ

Hook�̏ꏊ��\������R�}���h��1.x����͂��������A2.x�ȍ~�͂Ȃ�����

~~~
grep call_hook -R *
~~~

�Ȃǂ̃R�}���h�ŌĂяo���ӏ��icall_hook���\�b�h�j���������āA�t��������K�v������B

Windows���̏ꍇ�́A�T�N���G�f�B�^��G�ۂ̐��K�\�������𗘗p����Ƃ悢�B


�����ɂ���Hook�ꗗ�F http://www.redmine.org/projects/redmine/wiki/Hooks_List

## Hook�̏������i���\�b�h�j

~~~
class PluginHook < Redmine::Hook::ViewListener
  def controller_issues_new_before_save(context = {})
    issue = context[:issue]
    issue.assigned_to = User.current
  end
end
~~~

�̂悤�ɁA `Redmine::Hook::ViewListener` ���p�������N���X��
�g������Hook�̖��O�Ń��\�b�h���쐬����B

Hook���\�b�h�̈����́A�A�z�z��œn�����̂� `context = {}` ���W���ɂȂ�͗l�B

����context�̒��ɂ́Acall_hook����n���ꂽ�e�l�������Ă���̂ŁA
call_hook�ł̃L�[���蓖�Ă��Q�Ƃ��āA�~�����l�����o���B

��{�I�ɂ͂���Hook���Ăяo�����󋵂ɉ������l�������Ă���B
�i�`�P�b�g�X�V�����̓r���������� :issue �Ƀ`�P�b�g������Ȃǁj

Hook�p�ɒ�`�����N���X�� init.rb �� require ���邱�ƁB
�t�@�C����lib�z���ɒu���B

## Hook�̏������iView�j

~~~
class PluginHook < Redmine::Hook::ViewListener
  render_on :view_layouts_base_body_bottom, :partial => 'foo/bar'
end
~~~

`Redmine::Hook::ViewListener` ���p�������N���X�� `render_on Hook��` ���`����B

:partial �� :file �A :template �Ȃǂ̌`���ŌĂяo��View�t�@�C�����w�肷��B

�����ł�render���\�b�h���Ăяo���Ă��邽�߁A render���\�b�h�Ŏg��������͈�ʂ�g����͂��B

�Ăяo���ꂽView�t�@�C���ł́A�Ăяo�����ŗ��p�ł��Ă����C���X�^���X�ϐ��i@�t���̕ϐ��j��
�p�����ė��p�ł���̂ŁA
��낤�Ǝv���� @issues �� @trackers �Ȃǂ̈ꗗ�n�����Q�Ƃ��ēY�킷�邱�Ƃ��\�B
