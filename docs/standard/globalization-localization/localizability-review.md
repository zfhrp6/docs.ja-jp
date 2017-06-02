---
title: "ローカライズ化の確認 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "国際対応アプリケーション、ローカライズ可能性"
  - "アプリケーション開発 [.NET Framework]、ローカライズ"
  - "ローカライズ可能性 [.NET Framework]"
  - "国際対応のアプリケーション [.NET Framework]、ローカライズ可能性"
  - "グローバリゼーション [.NET Framework]、ローカライズ可能性"
  - "カルチャ、ローカライズ可能性"
  - "ローカリゼーション [.NET Framework]、ローカライズ可能性"
  - "グローバル アプリケーション、ローカライズ可能性"
  - "ローカライズ (リソースを)"
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# ローカライズ化の確認
ローカライズ対象の確認は、国際対応アプリケーションの開発中間ステップです。  グローバライズ済みアプリケーションがローカライズ可能であるかをチェックし、ユーザー インターフェイスのコードや特別な処理を必要とする要素を特定することができます。  この手順では、ローカリゼーション プロセス機能がアプリケーションに問題がないことを確認できます。  ローカライズ対象の確認によって発生させるすべての問題が扱われたら、アプリケーションはローカライズ可能です。  ローカライズ対象の確認が終わったら、ローカリゼーション プロセス中にソース・コードを変更する必要がありません。  
  
 ローカライズ対象の確認は、3 種類のチェックで構成されます。T:  
  
-   [グローバリゼーションの手法が実装されます。](#global)  
  
-   [カルチャに依存したな機能が正しく処理されます。](#culture)  
  
-   [International Data でアプリケーションをテストしているか。](#test)  
  
<a name="global"></a>   
## グローバリゼーションの推奨事項を実装する  
 対象のローカリゼーションを使用してアプリケーションを実行すると、[グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md) のトピックで説明されている推奨事項に設計および開発するローカライズ対象の確認は主に、品質保証のパスです。  それ以外の場合、この段階で [グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)"を確認し、実装するようにローカリゼーションを防ぐソース・コード内のエラーを修正します。  
  
<a name="culture"></a>   
## カルチャに依存した機能を処理する  
 .NET Framework は、カルチャによって大きく異なる複数の領域をプログラムではサポートされません。  ほとんどの場合、次のようなハンドル機能領域にカスタム コードを記述する必要があります:  
  
-   アドレス。  
  
-   電話番号。  
  
-   用紙サイズ。  
  
-   長さ、Weight、区分、ボリューム、温度に使用する測定単位。  .NET Framework が測定単位の変換のための組み込みサポートを提供しませんが、次の例に示すように、特定の国または地域のメトリック表記を使用するかどうかを判断するために <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=fullName> のプロパティを使用できます。  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## アプリケーションをテストする  
 アプリケーションをローカライズする前に、オペレーティング システムの各国語バージョンの各種言語のデータを使用して、アプリケーションをテストする必要があります。  ユーザー インターフェイスのほとんどはこの時点でローカライズされないが、次のような問題を検出する:  
  
-   オペレーティング システムのバージョンで正しく逆シリアル化せず、シリアル化されたデータ。  
  
-   現在のカルチャの規則を反映する数値データ。  たとえば、数が正しい桁区切り記号、小数点記号、または通貨記号と表示される場合があります。  
  
-   現在のカルチャの規則を反映する日付と時刻のデータ。  たとえば、月を表し、日が誤った順序で使用できる数値日付の区切り記号は正しくない場合があります。また、タイム ゾーン情報が正しくない場合があります。  
  
-   アプリケーションの既定のカルチャを指定しなかったため検出できないリソース。  
  
-   特定のカルチャの異なる順序で表示される文字列。  
  
-   同等の文字列比較または比較はに予想外の結果が生じます。  
  
 アプリケーション、処理されたカルチャに依存したな機能を適切に開発する場合、テストの実行中に発生したローカリゼーション問題で識別され、対処してグローバリゼーションの推奨事項に従っている場合、次の手順 [ローカリゼーション](../../../docs/standard/globalization-localization/localization.md)、に進むことができます。  
  
## 参照  
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)   
 [ローカリゼーション](../../../docs/standard/globalization-localization/localization.md)   
 [グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)   
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)