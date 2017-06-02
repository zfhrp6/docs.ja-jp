---
title: "型のメンバーの名前 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "イベント [.NET Framework] の名前"
  - "名前のメソッド [.NET Framework]"
  - "型のメンバー"
  - "[.NET Framework] ダイアログ ボックスのプロパティ名"
  - "フィールド名"
  - "フィールド名"
  - "型のメンバーの名前 [.NET Framework]"
  - "型のメンバー [.NET Framework]"
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 型のメンバーの名前
メンバーの型が加えられた: メソッド、プロパティ、イベント、コンス トラクター、およびフィールドです。 次のセクションでは、型のメンバーの名前付けのガイドラインについて説明します。  
  
## メソッドの名前  
 メソッドはアクションを実行する手段になっているために、デザインのガイドラインは動詞または動詞句メソッド名にすることが必要です。 またこのガイドラインに従うとは、メソッドの名前に名詞または形容詞句であるプロパティと型の名前を区別するために機能します。  
  
 **✓ は** 動詞または動詞句であるメソッドの名前を付けます。  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
  
```  
  
## プロパティの名前  
 その他のメンバーとは異なりは、名詞句または形容詞名にプロパティを指定する必要があります。 プロパティは、データを参照し、プロパティの名前に反映されるためです。 プロパティ名は、pascal 表記を使用が常に使用されます。  
  
 **✓ は** 名詞、名詞句、または形容詞として解釈を使用してプロパティを指定します。  
  
 **X のしないで** 次の例のように、"Get"メソッドの名前に一致するプロパティがあります。  
  
 `public string TextWriter { get {...} set {...} }`   
 `public string GetTextWriter(int value) { ... }`  
  
 このパターンでは、通常、プロパティが、メソッドを実際にする必要がありますを示します。  
  
 **✓ は** "List"または「コレクション」の前に、単数形の語句を使用する代わりにコレクション内の項目を記述する複数形の語句でコレクションのプロパティの名前  
  
 **✓ は** 肯定フレーズでブール型プロパティの名前 \(`CanSeek` の代わりに `CantSeek`\)。 ブール型プロパティもプレフィックスを必要に応じて、"Is"と"、"したり、「は、」値を追加する場合に限定します。  
  
 **✓ を検討してください** プロパティの型と同じ名前を提供します。  
  
 たとえば、次のプロパティ正しく取得および設定という名前の列挙値 `Color`, プロパティの名前を指定するため、 `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## イベントの名前  
 イベントは、常に何らかのアクションでは、いずれかの問題であるか、1 つが発生したことを指します。 そのためと同様にメソッド、イベントが、動詞と名前付き動詞の時制を使用して、イベントが発生すると時間を指定します。  
  
 **✓ は** イベントの名前は動詞または動詞句にします。  
  
 例としては、 `Clicked`, 、`Painting`, 、`DroppedDown`, 、という具合です。  
  
 **✓ は** 現在と過去時制を使用しての前後の概念でイベントの名前を付けます。  
  
 たとえば、ウィンドウが閉じられる前に発生する close イベントが呼び出されます `Closing`, 、ウィンドウが閉じられた後に発生する 1 つと呼ばれる、 `Closed`です。  
  
 **X のしないで** "Before"または"After"プレフィックスまたは postfixes を示す前と後のイベントを使用します。 使用して現在と過去時制前述のようです。  
  
 **✓ は** "EventHandler"サフィックスを持つイベント ハンドラー \(デリゲートがイベントの種類として使用\) という名前を次の例で示すようにします。  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ は** という名前の 2 つのパラメーターを使用して `sender` と `e` イベント ハンドラーにします。  
  
 Sender パラメーターでは、イベントを発生させたオブジェクトを表します。 型の sender パラメーターは、通常 `object`, より具体的な種類を使用することはあっても、です。  
  
 **✓ は** イベントという名前を"EventArgs"サフィックスを持つ引数クラスです。  
  
## フィールドの名前  
 フィールドの名前付けのガイドラインは、静的なパブリック、プロテクト フィールドに適用されます。 内部、プライベート フィールドが、ガイドラインが対応していないとでは、パブリックまたはプロテクトのインスタンス フィールドは許可されていない、 [メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)します。  
  
 **✓ は** フィールド名に pascal 表記を使用を使用します。  
  
 **✓ は** 名詞、名詞句、または形容詞として解釈を使用してフィールドの名前します。  
  
 **X のしないで** フィールド名にプレフィックスを使用します。  
  
 たとえば、使わない「g \_」または「s \_」を静的フィールドを示します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)