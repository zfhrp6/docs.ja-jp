---
title: 名前空間の名前
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0b6c5ac60474cfe984b3802e880eb58b017722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576433"
---
# <a name="names-of-namespaces"></a>名前空間の名前
として他の名前付けのガイドラインに目標の名前空間の名前を付けるときを作成するための十分なわかりやすくするためにどのような名前空間のコンテンツがある可能性がすぐにわかるフレームワークを使用するプログラマにとってです。 次のテンプレートは、名前空間の名前付けに関する一般的な規則を指定します。  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 例を次に示します。  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ しないで**から同じ名前を持つ異なる会社から名前空間を防ぐために、会社名と名前空間名をプレフィックスします。  
  
 **✓ しないで**名前空間の名前の 2 番目のレベルで、安定したバージョンに依存しない製品名を使用します。  
  
 **X しないで**企業内のグループ名は、短時間である傾向があるため、名前空間の階層内の名前の基準として組織階層を使用します。 関連するテクノロジのグループの周囲の名前空間の階層を整理します。  
  
 **✓ 操作を行います**をピリオド pascal 表記を使用、および別の名前空間のコンポーネントを使用して (例: `Microsoft.Office.PowerPoint`)。 会社をブランド化は、従来とは異なる大文字と小文字を使用している場合は、標準の名前空間の大文字と小文字から以上逸脱している場合でも、ブランド名で定義されている大文字小文字の区別に従ってください。  
  
 **✓ を検討してください**適切な場所に複数形の名前空間の名前を使用します。  
  
 たとえば、使用して`System.Collections`の代わりに`System.Collection`です。 ブランド名や頭字語は、この規則の例外をただしです。 たとえば、使用して`System.IO`の代わりに`System.IOs`です。  
  
 **X しないで**その名前空間、名前空間と型に同じ名前を使用します。  
  
 たとえば、使用しないでください`Debug`、名前空間と名前を指定し、という名前のクラスも提供`Debug`同じ名前空間。 いくつかのコンパイラでは、完全に修飾するには、このような型が必要です。  
  
### <a name="namespaces-and-type-name-conflicts"></a>名前空間と型名の競合  
 **X しないで**など、ジェネリック型の名前を導入`Element`、 `Node`、 `Log`、および`Message`です。  
  
 名前を入力する可能性は競合シナリオで共通の非常に高い確率があります。 ジェネリック型の名前を修飾する必要があります (`FormElement`、 `XmlNode`、 `EventLog`、 `SoapMessage`)。  
  
 別のカテゴリの名前空間の型名の競合を回避するための特定のガイドラインがあります。  
  
-   **アプリケーション モデルの名前空間**  
  
     1 つのアプリケーション モデルに属している名前空間は、一緒に使用ほとんどの場合が、他のアプリケーション モデルの名前空間を使用することはほぼありません。 たとえば、<xref:System.Windows.Forms?displayProperty=nameWithType>と共に名前空間が使用する非常にまれ、<xref:System.Web.UI?displayProperty=nameWithType>名前空間。 モデルの名前空間のよく知られているアプリケーション グループの一覧を次に示します。  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X しないで**1 つのアプリケーション モデル内の名前空間の型に同じ名前を指定します。  
  
     たとえば、という名前の型を追加しない`Page`を<xref:System.Web.UI.Adapters?displayProperty=nameWithType>名前空間、ため、<xref:System.Web.UI?displayProperty=nameWithType>名前空間には既にという名前の型が含まれています`Page`です。  
  
-   **インフラストラクチャの名前空間**  
  
     このグループには、ほとんどの一般的なアプリケーションの開発時にインポートされる名前空間が含まれています。 たとえば、`.Design`ツール プログラミングを開発する場合は名前空間が主に使用します。 これらの名前空間内の型との競合を回避することは、重要ではありません。  
  
-   **コア名前空間**  
  
     コア名前空間には、すべてが含まれて`System`名前空間、アプリケーション モデルの名前空間とインフラストラクチャの名前空間を除外します。 その他のコア名前空間が含まれます`System`、 `System.IO`、 `System.Xml`、および`System.Net`です。  
  
     **X しないで**付与がコア名前空間の型と競合する名前を入力します。  
  
     たとえば、使用しないで`Stream`型名として。 競合する<xref:System.IO.Stream?displayProperty=nameWithType>、非常によく型を使用します。  
  
-   **テクノロジ名前空間のグループ**  
  
     このカテゴリには、同じ最初の 2 つの名前空間ノードを持つすべての名前空間が含まれています。 `(<Company>.<Technology>*`)、など`Microsoft.Build.Utilities`と`Microsoft.Build.Tasks`です。 1 つのテクノロジに属している型が互いに競合しないことが重要です。  
  
     **X しないで**1 つのテクノロジ内の他の種類と競合する型の名前を割り当てます。  
  
     **X しないで**(場合を除く、テクノロジは、アプリケーション モデルで使用するものではありません) テクノロジの名前空間の型と、アプリケーション モデルの名前空間の型名の競合を紹介します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
