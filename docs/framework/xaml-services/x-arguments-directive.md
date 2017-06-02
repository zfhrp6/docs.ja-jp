---
title: "x:Arguments Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "x:Arguments directive [XAML Services]"
  - "Arguments directive in XAML [XAML Services]"
  - "XAML [XAML Services], x:Arguments directive"
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Arguments Directive
XAML の既定以外のコンストラクター オブジェクト要素の宣言またはファクトリ メソッド オブジェクトの宣言の構築引数をパッケージ化します。  
  
## XAML 要素の使用方法 \(既定以外のコンストラクター\)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 要素の使用方法 \(ファクトリ メソッド\)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|既定以外のバッキング コンストラクターまたはファクトリ メソッドに渡される引数を指定する 1 つ以上のオブジェクト要素。<br /><br /> 標準的な使用法としては、オブジェクト要素内で初期化テキストを使用して、実際の引数値を指定します。  「例」のセクションを参照してください。<br /><br /> 要素の順序は重要です。  XAML 型の順序は、バッキング コンストラクターまたはファクトリ メソッド オーバーロードの型および型の順序に一致している必要があります。|  
|`methodName`|`x:Arguments` の引数を処理するファクトリ メソッドの名前。|  
  
## 依存関係  
 `x:FactoryMethod` は、`x:Arguments` が適用されるスコープと動作を修正できます。  
  
 `x:FactoryMethod` が指定されていない場合は、`x:Arguments` はバッキング コンストラクターの別の \(既定以外の\) シグネチャに適用されます。  
  
 `x:FactoryMethod` が指定されている場合は、`x:Arguments` は名前付きメソッドのオーバーロードに適用されます。  
  
## 解説  
 XAML 2006 では、既定以外の初期化が、初期化テキストを通じてサポートされます。  ただし、初期化テキストの構築方法の実用的な用途には限界があります。  初期化テキストは単一のテキスト文字列として扱われます。したがって、追加される機能は、単一のパラメーターの初期化に限られます \(コンストラクターの動作に型コンバーターが定義され、文字列からカスタム情報項目とカスタム区切り記号を解析できる場合を除く\)。  また、オブジェクト ロジックへのテキスト文字列は、実際の文字列以外のプリミティブ向けに指定された XAML パーサーの、ネイティブの既定の型コンバーターであることがあります。  
  
 `x:Arguments` XAML の使用方法は、一般的な意味合いにおけるプロパティ要素の使用方法ではありません。これは、ディレクティブのマークアップは、格納オブジェクトの要素の型を参照しないためです。  これは、マークアップを子コンテンツの既定以外として解釈する必要がある範囲が要素によって区切られる、`x:Code` などの他のディレクティブに似ています。  この場合、各オブジェクト要素の XAML 型が、引数の型に関する情報を伝達します。XAML パーサーはこの情報を基に、`x:Arguments` の使用を通じて参照しようとしているコンストラクター ファクトリ メソッドの具体的なシグネチャを特定します。  
  
 構築するオブジェクト要素の `x:Arguments` は、他の \(そのオブジェクト要素の\) あらゆるプロパティ要素、コンテンツ、内部テキスト、または初期化文字列の前に配置する必要があります。  `x:Arguments` 内のオブジェクト要素には、XAML 型とそのバッキング コンストラクターまたはファクトリ メソッドによって許容される属性と初期化文字列を含めることができます。  オブジェクトまたは引数に関しては、確立されているプレフィックス マッピングを参照することによって、カスタム XAML 型、つまり既定の XAML 名前空間に属さない XAML 型を指定できます。  
  
 XAML プロセッサは、`x:Arguments` に指定された引数をオブジェクトの構築に使用するかどうかを、次のガイドラインによって判断します。  `x:FactoryMethod` が指定されている場合、指定された `x:FactoryMethod` との間で情報が比較されます。`x:FactoryMethod` の値はメソッド名であり、名前付きメソッドはオーバーロードを持つことができるという点に注意してください。  `x:FactoryMethod` が指定されていない場合、そのオブジェクトのすべてのパブリック コンストラクター オーバーロードとの間で情報が比較されます。  その後、XAML 処理ロジックは、パラメーターの数を比較し、対応するアリティを持ったオーバーロードを選択します。  複数の一致がある場合、XAML プロセッサは、指定されたオブジェクト要素の XAML 型に基づいてパラメーターの型を比較します。  引き続き複数の一致がある場合、XAML プロセッサの動作は定義されていません。  `x:FactoryMethod` は指定されているが、メソッドを解決できない場合、XAML プロセッサは例外をスローします。  
  
 XAML 属性の使用方法 `<x:Arguments>string</x:Arguments>` は技術的には可能です。  しかし、この方法に、初期化テキストと型コンバーターを使って実現できる以上の機能はなく、また、この構文は、XAML 2009 ファクトリ メソッドの機能を意図して設計されたものでもありません。  
  
## 例  
 次の例では、既定以外のコンストラクター シグネチャと、そのシグネチャに XAML でアクセスする `x:Arguments` の使用法を示しています。  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 次の例では、ターゲット ファクトリ メソッドのシグネチャと、そのシグネチャに XAML でアクセスする `x:Arguments` の使用法を示しています。  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## 参照  
 [Defining Custom Types for Use with .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)   
 [XAML の概要 \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)