---
title: x:Arguments ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564879"
---
# <a name="xarguments-directive"></a>x:Arguments ディレクティブ
XAML では、既定以外のコンス トラクター オブジェクト要素の宣言またはファクトリ メソッドのオブジェクトの宣言は、パッケージ構築引数。  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>XAML 要素の使用 (既定以外のコンス トラクター)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 要素の使用 (factory method)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|既定以外のバッキング コンス トラクターまたはファクトリ メソッドに渡される引数を指定する 1 つまたは複数のオブジェクト要素。<br /><br /> 一般的な使用では、実際の引数の値を指定するオブジェクトの要素内で初期化のテキストを使用します。 例のセクションを参照してください。<br /><br /> 要素の順序は重要です。 XAML の型の順序では、型と一致する必要があり、バッキング コンス トラクターまたはファクトリ メソッドのオーバー ロードの順序を入力します。|  
|`methodName`|いずれかを処理するファクトリ メソッドの名前`x:Arguments`引数。|  
  
## <a name="dependencies"></a>依存関係  
 `x:FactoryMethod` スコープと動作を変更することができます、`x:Arguments`適用されます。  
  
 ない場合は`x:FactoryMethod`が指定されている`x:Arguments`バッキング コンス トラクターの代替の (既定値) のシグネチャに適用されます。  
  
 場合`x:FactoryMethod`が指定されている`x:Arguments`名前のメソッドのオーバー ロードに適用されます。  
  
## <a name="remarks"></a>コメント  
 XAML 2006 では、初期化のテキストを既定以外の初期化をサポートできます。 ただし、初期化のテキストの構築方法の実用的なアプリケーションは制限されます。 初期化のテキストが 1 つのテキスト文字列として扱われますそのため、カスタム情報項目と、文字列からカスタムの区切り記号を解析できる構築動作の型コンバーターが定義されていない場合、1 つのパラメーターの初期化の機能のみ追加します。 また、オブジェクトのロジックをテキスト文字列を場合は true。 文字列以外のプリミティブを処理するための特定の XAML パーサーのネイティブの既定の型コンバーターにすることがあります。  
  
 `x:Arguments` XAML の使用法がプロパティ要素の使用、一般的な意味で、ディレクティブのマークアップが含まれるオブジェクト要素の型を参照していないためです。 では他のディレクティブなど`x:Code`要素に子コンテンツの既定値以外にするマークアップを解釈する範囲境界を定めます場所。 オブジェクトの各要素の XAML の型がどの特定のコンス トラクターのファクトリ メソッドのシグネチャを決定する、XAML パーサーで使用される引数の型に関する情報がどのように通信するこの例では、`x:Arguments`参照しようとして使用します。  
  
 `x:Arguments` オブジェクト要素の構築される必要がありますの前に、他のプロパティ要素、コンテンツ、内部のテキスト、またはオブジェクト要素の初期化の文字列。 内のオブジェクト要素`x:Arguments`その XAML の型とそのバッキング コンス トラクターまたはファクトリ メソッドによって許可されている属性および初期化文字列を含むことができます。 オブジェクトまたは引数のいずれかのカスタム XAML の型または外側にあるそれ以外の場合、既定の XAML 名前空間によって確立されたプレフィックスのマッピングを参照する XAML の型を指定できます。  
  
 XAML プロセッサに引数を指定する方法を決定する、次のガイドラインを使用して`x:Arguments`オブジェクトを構築するために使用する必要があります。 場合`x:FactoryMethod`が指定されている情報と比較を指定した`x:FactoryMethod`(なおの値`x:FactoryMethod`メソッド名であり、名前付きメソッドはオーバー ロードを持つことができます。 場合`x:FactoryMethod`が指定されていない、一連のオブジェクトのすべてのパブリック コンス トラクター オーバー ロードに情報を比較します。 XAML の処理ロジックは、パラメーターの数を比較し、アリティが一致するオーバー ロードを選択します。 複数の一致がある場合、XAML プロセッサは必要があります指定されたオブジェクトの要素の XAML の型に基づくパラメーターの型を比較します。 複数のまま 1 つの一致がある場合は、XAML プロセッサの動作は定義されません。 場合、`x:FactoryMethod`が指定されているメソッドを解決することはできませんが、XAML プロセッサは、例外をスローする必要があります。  
  
 XAML 属性の使用方法`<x:Arguments>string</x:Arguments>`は技術的に可能です。 ただし、これにより、ありませんでした何それ以外の場合の初期化のテキストと型コンバーターを使ってれない機能と、この構文を使用して XAML 2009 のファクトリ メソッドの機能の目的で設計ではありません。  
  
## <a name="examples"></a>使用例  
 次の例は、署名、次の XAML の使用方法に既定以外のコンス トラクターを示します`x:Arguments`そのシグネチャにアクセスします。  
  
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
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 次の例では、ターゲット工場出荷時のメソッド シグネチャでは、次の XAML の使用方法を示しています。`x:Arguments`そのシグネチャにアクセスします。  
  
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
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework XAML サービスで使用するためのカスタム型の定義](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
