# avue-crud

## 数据字典使用

```
{
      label: '人员部门',
      prop: 'deptId',
      sortable: true,
      minWidth: "100px",
      dicUrl: "/admin/dept/tree",
      props: {
        label: "deptName",
        value: "id",
        children: "children"
      }
    },
    
```

```
{
      label: '性别',
      prop: 'visitSex',
      sortable: true,
      minWidth: "100px",
      type: "select",
      dataType: 'number',
      dicUrl: '/admin/dict/type/sys_user_sex',
      dataType: "number",
    },
```

# avue-form

## 数据字典的使用
树下拉选择框
```
{
          label: "归属机构",
          prop: "deptId",
          type: "tree",
          rules: [{
            required: true,
            message: "归属机构不能为空",
            trigger: "blur"
          }],
          dicUrl: "/admin/dept/tree",
          props: {
            label: "deptName",
            value: "id",
            children: "children"
          }
        },
```

# avue-crud
表格行高亮显示
```
tableOption:{
 highlightCurrentRow: true, //点击行高亮
}
```
