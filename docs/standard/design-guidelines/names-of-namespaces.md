---
title: "名前空間の名前 | Microsoft Docs"
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
  - "名前 [.NET Framework] の競合"
  - "名前空間の名前 [.NET Framework]"
  - "型名の競合"
  - "名前空間 [.NET Framework] の名前"
  - "型名の名前 [.NET Framework]"
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 名前空間の名前
として他の名前付けのガイドラインと名前空間の名前を付けるときの目標を作成するための十分なわかりやすくするためにどのような名前空間のコンテンツがある可能性がすぐにわかるフレームワークを使用するプログラマにとってします。 次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 例を次に示します。  
  
 `Fabrikam.Math`   
 `Litware.Security`  
  
 **✓ は** 名前空間名を同じ名前の異なる会社から名前空間を防ぐために会社名のプレフィックスします。  
  
 **✓ は** 名前空間の名前の 2 番目のレベルで、バージョンに依存しない安定した製品名を使用します。  
  
 **X のしないで** 企業内のグループ名の有効期間の短いする傾向があるため、名前空間の階層内の名前の基準として組織階層を使用します。 関連するテクノロジのグループの周囲の名前空間の階層を整理します。  
  
 **✓ 操作を行います** 期間が設定された、pascal 表記を使用し、別の名前空間のコンポーネントを使用して \(例: `Microsoft.Office.PowerPoint`\)。 お客様のブランドは、従来とは異なる大文字と小文字を使用している場合は、一般的な名前空間の大文字と小文字から以上逸脱している場合でも、ブランドで定義された大文字と小文字に従ってください。  
  
 **✓ を検討してください** 適切な場所に複数形の名前空間の名前を使用します。  
  
 たとえば、使用して `System.Collections` の代わりに `System.Collection`します。 ブランド名や略語は、この規則の例外をただしです。 たとえば、使用して `System.IO` の代わりに `System.IOs`します。  
  
 **X のしないで** その名前空間、名前空間と型に同じ名前を使用します。  
  
 たとえば、使用しないでください `Debug` 、名前空間と名前を指定し、またという名前のクラスを提供 `Debug` 同じ名前空間。 いくつかのコンパイラでは、完全に修飾するには、このような型が必要です。  
  
### 名前空間と型名の競合  
 **X のしないで** など、ジェネリック型の名前が導入 `Element`, 、`Node`, 、`Log`, 、および `Message`です。  
  
 名前を入力する可能性は競合シナリオで共通の非常に高い確率があります。 ジェネリック型の名前を修飾する必要があります \(`FormElement`, 、`XmlNode`, 、`EventLog`, 、`SoapMessage`\)。  
  
 異なるカテゴリの名前空間の型名の競合を回避するための特定のガイドラインがあります。  
  
-   **アプリケーション モデルの名前空間**  
  
     1 つのアプリケーション モデルに属する名前空間は同時に、非常によく使用しますが、他のアプリケーション モデルの名前空間と併用することはほぼありません。 たとえば、 <xref:System.Windows.Forms?displayProperty=fullName> と共に名前空間が使用する非常にまれ、 <xref:System.Web.UI?displayProperty=fullName> 名前空間。 よく知られているアプリケーション モデルの名前空間のグループの一覧を次に示します。  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X のしないで** 1 つのアプリケーション モデル内で名前空間の型に同じ名前を指定します。  
  
     たとえば、という名前の型を追加しない `Page` に、 <xref:System.Web.UI.Adapters?displayProperty=fullName> 名前空間、ため、 <xref:System.Web.UI?displayProperty=fullName> 名前空間に既にという名前の型が含まれています `Page`します。  
  
-   **インフラストラクチャの名前空間**  
  
     このグループには、あまり一般的なアプリケーションの開発時にインポートされる名前空間が含まれています。 たとえば、 `.Design` ツールのプログラミングの開発時に名前空間が主に使用します。 これらの名前空間内の型との競合の回避は重要ではありません。  
  
-   **コア名前空間**  
  
     すべてのコア名前空間を含める `System` 名前空間、アプリケーション モデルの名前空間とインフラストラクチャの名前空間を除外します。 その他のコア名前空間が含まれます `System`, 、`System.IO`, 、`System.Xml`, 、および `System.Net`です。  
  
     **X のしないで** を指定します。 コア名前空間のすべての型と競合する名前を入力します。  
  
     たとえば、使用しないで `Stream` 型名として。 競合する <xref:System.IO.Stream?displayProperty=fullName>, 、非常によく型を使用します。  
  
-   **テクノロジ名前空間のグループ**  
  
     このカテゴリには、同じ最初の 2 つの名前空間ノードを持つすべての名前空間が含まれています。 `(<Company>.<Technology>*`\)、など `Microsoft.Build.Utilities` と `Microsoft.Build.Tasks`です。 1 つのテクノロジに属している型が互いに競合しないことが重要です。  
  
     **X のしないで** 1 つのテクノロジでは、他の種類と競合する型の名前を割り当てます。  
  
     **X のしないで** \(ない場合、このテクノロジは、アプリケーション モデルで使用するものではありません\) テクノロジの名前空間の型とのアプリケーション モデルの名前空間の型名の競合が発生します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)