import React, { useState } from 'react';

const PictureSelect = ({ pictures, value, onChange }) => {
  return (
    <div style={{ display: 'flex' }}>
      {pictures.map((item) => (
        <div key={item.id} style={{ position: 'relative' }}>
          <input
            type='checkbox'
            style={{ position: 'absolute', top: '10px', left: '10px' }}
            checked={value.indexOf(item.id) > -1}
            onChange={(e) => {
              if (e.currentTarget.checked) {
                onChange([...value, item.id]);
              } else {
                onChange(value.filter((id) => id != item.id));
              }
            }}
          />
          <img
            src={item.url}
            alt={item.name}
            style={{ maxWidth: '200px', maxHeight: '200px' }}
          />
        </div>
      ))}
    </div>
  );
};

const Page = () => {
  const [value, setValue] = useState(['1']);
  const pictures = [
    {
      id: '1',
      name: 'foo',
      url: 'https://gw.alipayobjects.com/mdn/rms_d212b7/afts/img/A*LlfeSa8N0WgAAAAAAAAAAABkARQnAQ'
    },
    {
      id: '2',
      name: 'foo',
      url: 'https://gw.alipayobjects.com/mdn/rms_d212b7/afts/img/A*LlfeSa8N0WgAAAAAAAAAAABkARQnAQ'
    },
    {
      id: '3',
      name: 'foo',
      url: 'https://gw.alipayobjects.com/mdn/rms_d212b7/afts/img/A*LlfeSa8N0WgAAAAAAAAAAABkARQnAQ'
    },
  ];
 // 同上面的数据
  console.log(value); // 输出用户选择图片 id。

  return (
    <PictureSelect
      pictures={pictures}
      value={value}
      onChange={(value) => setValue(value)}
    />
  );
};

export default Page;

