---
order: 6
title: 可展开
---

利用在 `ng-template` 定义 `#expand` 模板等于实现可展开，允许接收 `item`、`index`、`column` 三个值。附加可实现：嵌套子表格。

```ts
import { Component } from '@angular/core';
import { STColumn } from '@delon/abc';

@Component({
  selector: 'app-demo',
  template: `
  <st [data]="users" [columns]="columns">
    <ng-template #expand let-item let-index="index" let-column="column">
      {{ item.description }}
    </ng-template>
  </st>
  `,
})
export class DemoComponent {
  users: any[] = Array(10)
    .fill({})
    .map((item: any, idx: number) => {
      return {
        id: idx + 1,
        name: `name ${idx + 1}`,
        age: Math.ceil(Math.random() * 10) + 20,
        description: `${idx +
          1}. My name is John Brown, I am 32 years old, living in New York No. 1 Lake Park.`,
      };
    });
  columns: STColumn[] = [
    { title: '编号', index: 'id' },
    { title: '姓名', index: 'name' },
    { title: '年龄', index: 'age' },
  ];
}
```
