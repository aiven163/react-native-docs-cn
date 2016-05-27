本组件可以在iOS和Android上渲染原生的选择器（Picker）。用例：
```js
<Picker
  selectedValue={this.state.language}
  onValueChange={(lang) => this.setState({language: lang})}>
  <Picker.Item label="Java" value="java" />
  <Picker.Item label="JavaScript" value="js" />
</Picker>
```

### 属性

<div class="props">
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="view"></a><a href="view.html#props">View
        props...</a> <a class="hash-link" href="#view">#</a></h4></div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="onvaluechange"></a>onValueChange <span
            class="propType">function</span> <a class="hash-link" href="#onvaluechange">#</a></h4>
        <div><p>某一项被选中时执行此回调。调用时带有如下参数：
        <ul>
            <li><code>itemValue</code>: 被选中项的<code>value</code>属性</li>
            <li><code>itemPosition</code>: 被选中项在picker中的索引位置</li>
	   	</ul>
        </p></div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="selectedvalue"></a>selectedValue <span
            class="propType">any</span> <a class="hash-link" href="#selectedvalue">#</a></h4>
        <div><p>默认选中的值。可以是字符串或整数。</p></div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="style"></a>style <span class="propType">pickerStyleType</span>
        <a class="hash-link" href="#style">#</a></h4></div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="testid"></a>testID <span
            class="propType">string</span> <a class="hash-link" href="#testid">#</a></h4>
        <div><p>用于在端对端测试中定位此视图。</p></div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="enabled"></a><span class="platform">android</span>enabled
        <span class="propType">bool</span> <a class="hash-link" href="#enabled">#</a></h4>
        <div><p>如果设为false，则会禁用此选择器。</p></div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="mode"></a><span class="platform">android</span>mode
        <span class="propType">enum('dialog', 'dropdown')</span> <a class="hash-link" href="#mode">#</a></h4>
        <div><p>在Android上，可以指定在用户点击选择器时，以怎样的形式呈现选项：</p>
            <ul>
                <li><code>dialog</code>（对话框形式）: 显示一个模态对话框。默认选项。</li>
                <li><code>dropdown</code>（下拉框形式）: 以选择器所在位置为锚点展开一个下拉框。</li>
            </ul>
        </div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="prompt"></a><span class="platform">android</span>prompt
        <span class="propType">string</span> <a class="hash-link" href="#prompt">#</a></h4>
        <div><p>设置选择器的提示字符串。在Android的对话框模式中用作对话框的标题。</p></div>
    </div>
    <div class="prop"><h4 class="propTitle"><a class="anchor" name="itemstyle"></a><span class="platform">ios</span>itemStyle
        <span class="propType">itemStylePropType</span> <a class="hash-link" href="#itemstyle">#</a></h4>
        <div><p>指定应用在每项标签上的样式。</p></div>
    </div>
    
    
    <div>
    	<p>Demo</p>
    	<p style="background:'#E0E0E0'>
    		'use strict';

const React = require('react');
const ReactNative = require('react-native');
const StyleSheet = require('StyleSheet');
const UIExplorerBlock = require('UIExplorerBlock');
const UIExplorerPage = require('UIExplorerPage');

const {
  Picker,
  Text,
  TouchableWithoutFeedback,
} = ReactNative;
const Item = Picker.Item;

const PickerExample = React.createClass({

  statics: {
    title: '<Picker>',
    description: 'Provides multiple options to choose from, using either a dropdown menu or a dialog.',
  },

  getInitialState: function() {
    return {
      selected1: 'key1',
      selected2: 'key1',
      selected3: 'key1',
      color: 'red',
      mode: Picker.MODE_DIALOG,
    };
  },

  render: function() {
    return (
      <UIExplorerPage title="<Picker>">
        <UIExplorerBlock title="Basic Picker">
          <Picker
            style={styles.picker}
            selectedValue={this.state.selected1}
            onValueChange={this.onValueChange.bind(this, 'selected1')}>
            <Item label="hello" value="key0" />
            <Item label="world" value="key1" />
          </Picker>
        </UIExplorerBlock>
        <UIExplorerBlock title="Disabled picker">
          <Picker style={styles.picker} enabled={false} selectedValue={this.state.selected1}>
            <Item label="hello" value="key0" />
            <Item label="world" value="key1" />
          </Picker>
        </UIExplorerBlock>
        <UIExplorerBlock title="Dropdown Picker">
          <Picker
            style={styles.picker}
            selectedValue={this.state.selected2}
            onValueChange={this.onValueChange.bind(this, 'selected2')}
            mode="dropdown">
            <Item label="hello" value="key0" />
            <Item label="world" value="key1" />
          </Picker>
        </UIExplorerBlock>
        <UIExplorerBlock title="Picker with prompt message">
          <Picker
            style={styles.picker}
            selectedValue={this.state.selected3}
            onValueChange={this.onValueChange.bind(this, 'selected3')}
            prompt="Pick one, just one">
            <Item label="hello" value="key0" />
            <Item label="world" value="key1" />
          </Picker>
        </UIExplorerBlock>
        <UIExplorerBlock title="Picker with no listener">
          <Picker style={styles.picker}>
            <Item label="hello" value="key0" />
            <Item label="world" value="key1" />
          </Picker>
          <Text>
            Cannot change the value of this picker because it doesn't update selectedValue.
          </Text>
        </UIExplorerBlock>
        <UIExplorerBlock title="Colorful pickers">
          <Picker
            style={[styles.picker, {color: 'white', backgroundColor: '#333'}]}
            selectedValue={this.state.color}
            onValueChange={this.onValueChange.bind(this, 'color')}
            mode="dropdown">
            <Item label="red" color="red" value="red" />
            <Item label="green" color="green" value="green" />
            <Item label="blue" color="blue" value="blue" />
          </Picker>
          <Picker
            style={styles.picker}
            selectedValue={this.state.color}
            onValueChange={this.onValueChange.bind(this, 'color')}
            mode="dialog">
            <Item label="red" color="red" value="red" />
            <Item label="green" color="green" value="green" />
            <Item label="blue" color="blue" value="blue" />
          </Picker>
        </UIExplorerBlock>
      </UIExplorerPage>
    );
  },
  changeMode: function() {
    const newMode = this.state.mode === Picker.MODE_DIALOG
        ? Picker.MODE_DROPDOWN
        : Picker.MODE_DIALOG;
    this.setState({mode: newMode});
  },
  onValueChange: function(key: string, value: string) {
    const newState = {};
    newState[key] = value;
    this.setState(newState);
  },
});
var styles = StyleSheet.create({
  picker: {
    width: 100,
  },
});
module.exports = PickerExample;
    	</p>
    </div>
    
</div>
