---
title: React ������
date: 2018-08-02 15:15:30
tags: react
---
### 1. React����������
###  ����������ڵ�����״̬չʾ�� 
- Mounting: �Ѳ���������dom�ṹ 
- Updating: ���ڱ�������Ⱦ 
- Unmounting: ���Ƴ�����ʵdom�ṹ

### 2.���� �������ڵĴ�������will��ʾ����״̬֮ǰ���ã�did��ʾ����״̬֮����ã���
- **componentWillMount()** :
�����Ҫ��Ⱦ����ʵdom�ڵ㣻ִ��һ�Σ��ڳ�ʼ��render֮ǰִ�У��������������ڵ���setState��render()֪��state�����仯������ִֻ��һ��
- **componentDidMount()**
//����Ѿ���Ⱦ����ʵdom�ڵ㣻�ڳ�ʼ��render֮��ִֻ��һ�Σ�����������ڣ����Է����κ������componentDidMount()�����е�������ڸ����֮ǰִ�У�
�����������ʼ���Ϳ��Ժ� js ������ܽ����ˣ��������ü�ʱ setTimeout ���� setInterval�����߷�����������
- **componentWillUpdate()**//��props��state�����仯�������Ҫ��������Ⱦ��������render����֮ǰִ�У���Ȼ��ʼ��renderʱ��ִ�и÷�������Ҫ�ر�ע����ǣ�������������棬��Ͳ���ʹ��this.setState���޸�״̬�������������֮�󣬾ͻ��nextProps��nextState�ֱ����õ�this.props��this.state�С�����������������ͻ����render()�����½�����
- **componentDidUpdate()**//����Ѿ����������Ⱦ���ڳ�ʼ��renderʱ��ִ��
- **componentWillUnmout()**//ж�������������ת·�ɵ�ʱ��
- **componentWillReceiveProps()** //�Ѿ��������props�����ı��ʱ����ã�������ص��������棬����Ը������Եı仯��ͨ������this.setState()������������״̬���ɵ����Ի��ǿ���ͨ��this.props����ȡ,������ø���״̬�ǰ�ȫ�ģ������ᴥ�������render����
- **shouldComponentUpdate()**//����ж��Ƿ�Ҫ������Ⱦ��ʱ����ã��ڳ�ʼ��renderʱ����ִ�У���props����state�����仯ʱִ�У���������render֮ǰ�����µ�props����state����Ҫ�������ʱ������false
#### 3. ��������������ڵ�ִ��˳�� ����ͼ��ʾ��
![image](https://note.youdao.com/yws/public/resource/ab2cc4cb6abd27779a98343b11256d86/xmlnote/D3F2B8C7A6A04D8F99722AF34EEA9F36/851A0C31E6A749EB948EE8F6B5C6E006/88)
### 3.react�������ĿӺ�һЩС��֪ʶ��:
#### - setState()���첽��:
this.setState()�����render�������������������ı�state��ֵ��state����render�����и�ֵ�ġ�
����ִ��this.setState()��������ȡstate��ֵ�ǲ���ġ�
ͬ����ֱ�Ӹ�ֵstate������������£���Ϊû�е���render������
#### - �������������
componentWillMount��componentDidMount ֻ���ڳ�ʼ����ʱ��ŵ��á�
componentWillReceivePorps��shouldComponentUpdate��componentWillUpdata��componentDidUpdate ֻ������ڸ��µ�ʱ��ű����ã���ʼ��ʱ�����á�
#### - reducer���뷵��һ���µĶ�����ܳ�������ĸ���
��Ϊ��connect�����л���¾�����state����ǳ�Աȣ����stateֻ��ֵ�ı䵫�����õ�ַû�иı䣬connect����Ϊ������ͬ�����������¡�
#### - ����reducer���ص�state�Ƿ�ı䣬subscribe��ע������лص��������ᱻ������
#### - �������������ĸ�����Ǵ�д�������������Ĺ淶��
#### - ���ж��֮ǰ������domԪ���ϵļ����¼����Ͷ�ʱ����Ҫ�ֶ��������Ϊ��Щ������react�Ŀ��Ʒ�Χ�ڣ������ֶ������
#### - �������ʱ��������ͨ��export default ��¶��ȥ����ôrequire.ensureʱ�������default��

```
require.ensure([], require => {
    cb(null, require('../Component/saleRecord').default)
},'saleRecord')
```
#### - react��·����hashHistory��browserHistory��hashHistory��hash#������ת��һ��������ʽ���ϲ���browserHistory������ͨ�ĵ�ַ��ת��һ�����ڿ����׶Ρ�
#### - ��ǩ���õ��ģ�for Ҫд��htmlFor����Ϊfor�Ѿ����˹ؼ��֡�
#### - componentWillUpdate�п���ֱ�Ӹı�state��ֵ����������setState��
#### - ���ʹ��es6class��̳�react��component�����constructor�б������super����Ϊ���������super�̳�component��this������ʵ������ʱ��ᱨ��
#### - ���ж��֮ǰ������domԪ���ϵļ����¼����Ͷ�ʱ����Ҫ�ֶ��������Ϊ��Щ������react�Ŀ��Ʒ�Χ�ڣ������ֶ������ָ������this.refs.xxx������ʵdom��addEventListener������ӵļ����¼��������ж�ص�ʱ��Ҫ�ֶ����(removeEventListener)��react����ϵ�onClick���ֲ��ùܣ�react�����Ǵ������