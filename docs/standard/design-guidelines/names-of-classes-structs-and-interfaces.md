---
title: "クラス、構造体、およびインターフェイスの名前 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "型名、ガイドライン"
  - "名前のクラス [.NET Framework]"
  - "列挙体 [.NET Framework] の名前"
  - "名前 [.NET Framework] インターフェイス"
  - "一般的な型名"
  - "型名の名前 [.NET Framework]"
  - "クラスの名前 [.NET Framework]"
  - "名前のインターフェイス [.NET Framework]"
  - "ジェネリック型パラメーター"
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# クラス、構造体、およびインターフェイスの名前
次の名前付けのガイドラインは、一般的な種類の名前付けに適用されます。  
  
 **✓ は** クラスと構造体には名詞または名詞句、pascal 表記を使用を使用して名前を付けます。  
  
 これは、動詞句とという名前のメソッドと型名を区別します。  
  
 **✓ は** 形容詞句、または場合によって名詞または名詞句のインターフェイスの名前します。  
  
 名詞と名詞句をめったに使用する必要があり、抽象クラスとインターフェイスではなく、型があることを示す可能性があります。  
  
 **X のしないで** クラス名のプレフィックス \("C"など\) を指定します。  
  
 **✓ を検討してください** 、基本クラスの名前のクラスを派生の名前を終了します。  
  
 これはとても読みにくいはであり、関係を明確に説明します。 コード内のいくつかの例に示します: `ArgumentOutOfRangeException`, が付いての `Exception`, 、および `SerializableAttribute`, が付いての `Attribute`です。 ただし、これは次のガイドラインを適用することで、適切な判断を使用するにはなど、 `Button` クラスは、一種の `Control` イベントが `Control` 名前に表示されません。  
  
 **✓ は** インターフェイス名のプレフィックス文字では、型がインターフェイスであることを示します。  
  
 たとえば、 `IComponent` \(わかりやすい名詞\) `ICustomAttributeProvider` \(名詞句\)、および `IPersistable` \(形容詞\) は適切なインターフェイス名。 同様に他の種類名の省略形を回避します。  
  
 **✓ は** だけで、"I"プレフィックスのインターフェイス名、クラスがインターフェイスの標準的な実装であるクラス – インターフェイスのペアを定義するときに名前が異なることを確認します。  
  
## ジェネリック型パラメーターの名前  
 ジェネリックは .NET Framework 2.0 に追加されました。 機能の導入と呼ばれる識別子の新しい種類 *パラメーター入力*します。  
  
 **✓ は** 1 文字の名前が完全に説明し、わかりやすい名前と値を追加していない限り、わかりやすい名前を持つジェネリック型パラメーターの名前します。  
  
 **✓ を検討してください** を使用して `T` 単一文字の型パラメーターが 1 つの型の型のパラメーター名として。  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 **✓ は** 説明的な型のパラメーター名のプレフィックス `T`します。  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 **✓ を検討してください** 制約を示す名前、パラメーターの型パラメーターに配置されます。  
  
 パラメーターに制約があるなど `ISession` という `TSession`します。  
  
## 一般的な種類の名前  
 **✓ は** から派生した、または特定の .NET Framework 型を実装する型の名前を付けるときは、次の表に記載されているガイドラインに従ってください。  
  
|基本データ型|型の派生と実装ガイドライン|  
|------------|-------------------|  
|`System.Attribute`|**✓ は** カスタム属性クラスの名前にサフィックス"Attribute"を追加します。 カスタム属性クラスの名前にサフィックス"Attribute"を追加します。|  
|`System.Delegate`|**✓ は** イベントで使用されているデリゲートの名前にサフィックス"EventHandler"を追加します。<br /><br /> **✓ は** 以外のイベント ハンドラーとして使用されているデリゲートの名前に"Callback"サフィックスを追加します。<br /><br /> **X のしないで** デリゲートに「Delegate」サフィックスを追加します。|  
|`System.EventArgs`|**✓ は** "EventArgs"サフィックスを追加|  
|`System.Enum`|**X のしないで** このクラスから派生、代わりに使用する言語でサポートされているキーワードを使用して、たとえば、C\# の場合、enum キーワードを使用します。<br /><br /> **X のしないで** 「列挙」または"Flag"サフィックスを追加|  
|`System.Exception`|**✓ は** 「例外」サフィックスを追加|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|**✓ は** 「辞書」サフィックスを追加 なお `IDictionary` は、コレクションの特定の型ですが、このガイドラインに依存している一般的なコレクション ガイドラインよりも優先されます。|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|**✓ は** 「コレクション」サフィックスを追加|  
|`System.IO.Stream`|**✓ は** 「ストリーム」サフィックスを追加|  
|`CodeAccessPermission IPermission`|**✓ は** 「アクセス」サフィックスを追加|  
  
## 列挙体の名前を付ける  
 一般に列挙型 \(列挙型とも呼ばれます\) の名前にすることは \(pascal 表記を使用など\) 標準的な型の名前付け規則に従う必要があります。 ただし、この列挙型に適用する追加のガイドラインがあります。  
  
 **✓ は** の値がビット フィールドでない場合は、列挙体の単数形の型名を使用します。  
  
 **✓ は** フラグ列挙体とも呼ばれます。 の値として、ビット フィールドを持つ列挙体の複数形の型名を使用します。  
  
 **X のしないで** 列挙型の型名で、「列挙」サフィックスを使用します。  
  
 **X のしないで** 「フラグの設定」を使用するか列挙型に"Flags"サフィックスが名前を入力します。  
  
 **X のしないで** リッチ テキストを持つ列挙型などの列挙値の名前 \(たとえば、"ad"ADO 列挙型にします。\)、"rtf"にプレフィックスを使用します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)