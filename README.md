# react-native-waterfall

a virtualized & infinite waterfall layout component for React-Native

## Getting started

`npm i react-native-virtualized-waterfall`

or

`yarn add react-native-virtualized-waterfall`

## Preview

[online-demo](https://codesandbox.io/s/waterfall-demo-rxkww?file=/src/App.tsx "Heading link")

related project: [h.bilibli-rn](https://github.com/Feng-Bu-Jue/h.bilibili-rn "Heading link")

![h.bilibili](https://i.loli.net/2020/09/02/mFa6XNckYn5UAvK.gif)

## Props

please refer to type definition

*This project layout through known item height,so you must got item size before render

## Usage

```Typescript
import Waterfall from "react-native-virtualized-waterfall";


fetchItems(columnWidth:number,reload:boolean=false): Promise<void> {
  //...fetch data and mapping to itemInfo
}

render(){
  return
    <Waterfall
        onInitData={(columnWidth) => this.fetchItems(columnWidth)}
        columnNum={2}
        columnGap={this.columnGap}
        itemInfoData={this.items} // 
        bufferAmount={10}
        renderItem={(
          {
            item,
            size,
          }: {
            item: any;
            size: number;
          },
          columnWidth: number,
        ) => {
          const ratio = 1;
          return (
              <Image
                style={{
                  height: size,
                  width: ratio * size,
                }}
                {...}
              />
          );
        }}
        onRefresh={(columnWidth) => {
          this.pageNum = 1;
          return this.fetchItems(columnWidth, true);
        }}
        onInfinite={(columnWidth) => this.fetchItems(columnWidth)} />
}
```
