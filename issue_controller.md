# �`�P�b�g����

## ������h���_

### �e�`�P�b�g�̐ݒ�

�e�`�P�b�g�ԍ����Q�Ƃ���ɂ́A `@issue.parent_id` ������΂������A
�������ꍇ�́A

~~~
@issue.parent_id = 1
~~~

�̂悤�ɏ����Ă��e�`�P�b�g��ύX�ł����A

~~~
@issue.parent_issue_id = 1
~~~

���g���K�v������B

~~~
@issue.safe_attributes = params[:issue]
~~~

�̂悤�Ȍ`�ő������ꍇ�����l�B

### �J�X�^���t�B�[���h

#### �֘A�N���X

CustomField: �J�X�^���t�B�[���h�i���ڗ��j

CustomValue: �J�X�^���t�B�[���h�ɓ����Ă���l

CustomFieldValue: �J�X�^���t�B�[���h�ƒl���Q�Ƃ��邽�߂̃N���X

#### ���\�b�h�i�`�P�b�g����Q�Ƃł�����́j

custom_fields: ����ȃ��\�b�h�͖���

custom_values: CustomValue�Ƃ�has_many�֘A�B

available_custom_fields: �`�P�b�g�̑S�ẴJ�X�^���t�B�[���h�i�v���W�F�N�g�Ŗ����Ȃ��̂��܂ށj

custom_field_values: ���ݒ�̃J�X�^���t�B�[���h�ɏ����l�����蓖��

visible_custom_field_values: custom_field_values�̓��A�{���\�Ȃ��݂̂̂ɍi�荞�ށi���[����\���ݒ�j