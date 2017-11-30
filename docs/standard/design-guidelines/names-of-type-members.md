---
title: "型のメンバーの名前"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1a3460b734d5bab6f5362fa9d3631e06821f6d49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-type-members"></a>型のメンバーの名前
メンバーの種類がされています: メソッド、プロパティ、イベント、コンス トラクター、およびフィールドです。 次のセクションでは、型のメンバーの名前付けのガイドラインについて説明します。  
  
## <a name="names-of-methods"></a>メソッドの名前  
 メソッドは操作を実行する手段であるため、デザインのガイドラインは、動詞または動詞句メソッド名にすることが必要です。 このガイドラインにも従うプロパティと型名を名詞または形容詞句からメソッド名を区別するために機能します。  
  
 **✓ しないで**動詞または動詞句は、メソッドの名前を指定します。  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>プロパティの名前  
 他のメンバーとは異なり名詞句または形容詞名に、プロパティを指定する必要があります。 プロパティが、データを参照し、プロパティの名前を反映するためです。 プロパティ名は、pascal 表記を使用が常に使用されます。  
  
 **✓ しないで**名詞、名詞句、または形容詞を使用してプロパティの名前を付けます。  
  
 **X しないで**次の例のように、"Get"メソッドの名前に一致するプロパティがあります。  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 このパターンでは、通常、プロパティがメソッドを実際にする必要がありますを示します。  
  
 **✓ しないで**後に"List"または"Collection"単数形の語句を使用する代わりに、コレクション内の項目を記述する複数形の語句でコレクションのプロパティの名前を付けます  
  
 **✓ しないで**肯定の語句でブール型プロパティの名前 (`CanSeek`の代わりに`CantSeek`)。 ブール型プロパティもプレフィックスを必要に応じて、"Is"と"、"したり"は、"値を追加する場合に限定します。  
  
 **✓ を検討してください**プロパティの型と同じ名前を提供します。  
  
 たとえば、次のプロパティ正しく取得および設定という名前列挙値`Color`ので、プロパティの名前が`Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>イベントの名前  
 イベントは、常に、何らかのアクションでは、いずれかの問題であるかが発生した 1 つを参照してください。 そのため、メソッド、イベント名前付けには、動詞と同様動詞の時制を使用するイベントが発生した時刻を指定します。  
  
 **✓ しないで**動詞または動詞句を持つイベントの名前を付けます。  
  
 例としては、 `Clicked`、 `Painting`、`DroppedDown`のようにします。  
  
 **✓ しないで**名前を指定してイベントの概念で前に、と後、現在および過去時制を使用します。  
  
 たとえば、クローズ イベントには、ウィンドウが閉じられる前に発生が呼び出されます`Closing`、ウィンドウが閉じられた後に発生する 1 つが呼び出されますと`Closed`です。  
  
 **X しないで**"Before"または"After"プレフィックスまたは postfixes を示す前と後イベントを使用します。 現在使用して上記の過去時制。  
  
 **✓ しないで**"EventHandler"サフィックスを持つイベント ハンドラー (デリゲートがイベントの種類として使用) という名前を次の例に示すようにします。  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ は**という 2 つのパラメーターを使用して`sender`と`e`イベント ハンドラーにおいてです。  
  
 送信元のパラメーターは、イベントを発生させたオブジェクトを表します。 型の送信元のパラメーターは、通常`object`場合より具体的な種類を使用することができます。  
  
 **✓ しないで**イベント引数クラス"EventArgs"サフィックスを持つ名前を付けます。  
  
## <a name="names-of-fields"></a>フィールドの名前  
 フィールドの名前付けのガイドラインは、パブリックおよびプロテクトの静的フィールドに適用します。 内部およびプライベート フィールドが、ガイドラインで対応されていないと、パブリックまたはプロテクトのインスタンス フィールドがによって許可されていません、[メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)です。  
  
 **✓ しないで**フィールドの名前で pascal 表記を使用を使用します。  
  
 **✓ しないで**名詞、名詞句、または形容詞を使用してフィールドの名前を付けます。  
  
 **X しないで**フィールド名にプレフィックスを使用します。  
  
 たとえば、使わない g「_」または「s _」を静的フィールドを示します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
