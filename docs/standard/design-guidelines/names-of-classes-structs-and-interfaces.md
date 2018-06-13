---
title: クラス、構造体、およびインターフェイスの名前
ms.date: 03/30/2017
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1841fbfcb76d5b56681b63ec4b39e9a7418707f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576143"
---
# <a name="names-of-classes-structs-and-interfaces"></a>クラス、構造体、およびインターフェイスの名前
次の名前付けのガイドラインは、一般的な種類の名前付けに適用されます。  
  
 **✓ しないで**名前をクラスと構造体には名詞または名詞句を使用して pascal 表記を使用します。  
  
 これは、動詞句とという名前のメソッドと型名を区別します。  
  
 **✓ しないで**形容詞句、または場合によっては名詞または名詞句とインターフェイスの名前します。  
  
 名詞や名詞句を付けることはほとんどなく、種類必要がある、抽象クラスとインターフェイスではなくを示している可能性があります。  
  
 **X しないで**クラス名のプレフィックス ("C"など) を指定します。  
  
 **✓ を検討してください**基底クラスの名前のクラスを派生の名前を終了します。  
  
 これは非常に読み取り可能であり、リレーションシップを明確に説明します。 コードでは次の例を示します:`ArgumentOutOfRangeException`は一種の`Exception`、および`SerializableAttribute`は一種の`Attribute`します。 ただし、することが重要です。 このガイドラインを適用することで、適切な判断たとえば、`Button`クラスは、一種の`Control`イベントが`Control`その名前が表示されません。  
  
 **✓ しないで**インターフェイス名のプレフィックス文字では、型がインターフェイスであることを示します。  
  
 たとえば、 `IComponent` (わかりやすい名詞) `ICustomAttributeProvider` (名詞句)、および`IPersistable`(形容詞) 適切なインターフェイス名は、します。 同様に他の種類名の省略形を回避します。  
  
 **✓ しないで**だけで、"I"プレフィックスのインターフェイスの名前、クラスがインターフェイスの標準的な実装であるクラス – インターフェイスのペアを定義するときに名前が異なることを確認してください。  
  
## <a name="names-of-generic-type-parameters"></a>ジェネリック型パラメーターの名前  
 ジェネリックは、.NET Framework 2.0 に追加されました。 機能には、新しいと呼ばれる識別子の種類が導入されました。*パラメーター入力*です。  
  
 **✓ しないで**1 文字の名前が完全にわかり、わかりやすい名前と値を追加していない場合を除き、わかりやすい名前を持つジェネリック型パラメーターの名前します。  
  
 **✓ を検討してください**を使用して`T`の 1 文字の型パラメーターを 1 つの種類の型パラメーター名として。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ しないで**説明的な型パラメーター名をプレフィックス`T`です。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ を検討してください**制約を示す名前、パラメーターの型パラメーター上に配置します。  
  
 など、パラメーターに対する制約として`ISession`という`TSession`です。  
  
## <a name="names-of-common-types"></a>一般的な種類の名前  
 **✓ しないで**から派生または特定の .NET Framework 型を実装する型の名前を付けるときは、次の表に説明されているガイドラインに従ってください。  
  
|基本型|派生実装する型のガイドライン|  
|---------------|------------------------------------------|  
|`System.Attribute`|**✓ しないで**カスタム属性クラスの名前にサフィックス"Attribute"を追加します。|  
|`System.Delegate`|**✓ しないで**イベントで使用されるデリゲートの名前にサフィックス"EventHandler"を追加します。<br /><br /> **✓ しないで**以外のイベント ハンドラーとして使用されているデリゲートの名前に"Callback"サフィックスを追加します。<br /><br /> **X しないで**「代理」サフィックスをデリゲートに追加します。|  
|`System.EventArgs`|**✓ しないで**"EventArgs です"というサフィックスを追加。|  
|`System.Enum`|**X しないで**代わりに使用する言語でサポートされているキーワードを使用して; たとえば、C# の場合、次のように使用します。 このクラスから派生、`enum`キーワード。<br /><br /> **X しないで**「列挙」または"Flag"サフィックスを追加|  
|`System.Exception`|**✓ しないで**"Exception"サフィックスを追加|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ しないで**「ディクショナリ」というサフィックスを追加。 なお`IDictionary`コレクションの特定の種類が、このガイドラインに続くコレクションのより一般的なガイドラインよりも優先されます。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ しないで**「コレクション」サフィックスを追加|  
|`System.IO.Stream`|**✓ しないで**「ストリームです」というサフィックスを追加。|  
|`CodeAccessPermission IPermission`|**✓ しないで**「権限」というサフィックスを追加。|  
  
## <a name="naming-enumerations"></a>列挙体の名前を付ける  
 一般に列挙型 (列挙型とも呼ばれます) の名前は、標準的な型の名前付け規則 (pascal 表記を使用など) を従う必要があります。 ただし、これには具体的には列挙型に適用される追加のガイドラインがあります。  
  
 **✓ しないで**ビット フィールドがその値がない限り、列挙体の単数形の型名を使用します。  
  
 **✓ しないで**ビット フィールドを持つ列挙体の複数形の型名を使用して値として、フラグ列挙型とも呼ばれます。  
  
 **X しないで**列挙型の型名で、「列挙」サフィックスを使用します。  
  
 **X しないで**「フラグを設定」を使用して、または"Flags"サフィックス列挙型では、名前を入力します。  
  
 **X しないで**リッチ テキストの列挙型などの列挙値の名前 (例:"ad"ADO 列挙型の場合。)、"rtf"に対して、プレフィックスを使用します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
