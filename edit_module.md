2.5.x�z��

# ���W���[���𑝂₷

�v���O�C���f�B���N�g���� `init.rb` ��
`Redmine::Plugin.register` ���\�b�h���Ɉȉ���ǉ�����

~~~
project_module :module_name do
  permission :permission_a, :controller_name => [:action_a, :action_b], {:option => :type}
  permission :view_foo, :foos => [:index, :show], :require => :member
end
~~~

�ȉ��A�Ή��\

|����            |����|
|----------------|---|
|:module_name    |���W���[�����B<br>Redmine�W���̃��W���[���⑼�̃v���O�C���Ɣ��Ȃ����O���悢�B<br>�����ɏ����Ȃ�v���O�C�����������͒񋟂���@�\�����p�ꂩ���[�}���ŁB|
|permission      |���W���[���ɑΉ����������̒�`�B<br>�Œ�ЂƂ͕K�{�H|
|:permission_a   |�������B|
|:controller_name|�Ăяo���R���g���[���̖��O�B IssuesController �Ȃ� :issues �̂悤�ɏ����B|
|option          |�C�Ӎ��ځB[[���[���̌����𑝂₷]] ���Q�l|

`config/locales/**.yml` �� `project_module_xxxx:` �ixxxx�̓��W���[�����j�����Ă�����
���W���[�������|�󂵂ĕ\�������B

## �֘A�@�\

[[init.rb]]
[[���[���̌����𑝂₷]]