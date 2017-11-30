---
title: "ローカライズ化の確認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a>ローカライズ化の確認
ローカライズ化の確認は、国際対応アプリケーションの開発での中間のステップです。 グローバライズされたアプリケーションがローカライズ可能なコードや特別な処理を必要とするようなユーザー インターフェイスの要素を識別することを確認します。 この手順では、こと、ローカリゼーション処理はされていない、機能上の欠陥をアプリケーションにすることを確認できます。 ローカライズ化の確認で発生したすべての問題が処理された、ときに、アプリケーションはローカライズ可能です。 ローカライズ化の確認が完全な場合は、ローカリゼーション処理中にすべてのソース コードを変更することはできません。  
  
 ローカライズ化の確認は、次の 3 つのチェックで構成されます。  
  
-   [グローバリゼーションの推奨事項が実装されているか。](#global)  
  
-   [カルチャに依存した機能が正しく処理されますか。](#culture)  
  
-   [各種言語データを使用してアプリケーションをテストするか。](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>グローバリゼーションの推奨事項を実装する  
 推奨事項が説明に従っている場合とデザインおよび注意でのローカライズを使用してアプリケーションを開発するが、[グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)資料、ローカリゼーション レビューは、品質保証パスに大きく左右されます. それ以外の場合、この段階を確認し、に関する推奨事項を実装する[グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)、およびソース コードのローカライズを妨げるエラーを修正します。  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>カルチャに依存した機能を処理する  
 .NET Framework では、多くのカルチャによって大きく異なる点でプログラムによるサポートは提供されません。 ほとんどの場合は、次のような機能領域を処理するカスタム コードを記述する必要。  
  
-   対応します。  
  
-   電話番号。  
  
-   用紙のサイズ。  
  
-   長さ、重量、領域、ボリューム、および温度を使用する測定単位です。 .NET Framework では、測定単位の間の変換用の組み込みのサポートは提供しません、使用すると、<xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType>プロパティを次の例に示すように、特定の国または地域がメートル法を使用するかどうかを決定します。  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>アプリケーションをテストする  
 アプリケーションをローカライズする前に、オペレーティング システムの各国語バージョンの国際対応データを使用してテストする必要があります。 この時点で、ユーザー インターフェイスの大部分はローカライズされません、ですが、次などの問題を検出することができます。  
  
-   シリアル化解除できません正しくオペレーティング システムのバージョン間でシリアル化されたデータ。  
  
-   現在のカルチャの規則を反映しない数値のデータです。 たとえば、数値は、不正確な桁区切り記号、桁区切り記号、または通貨記号と表示があります。  
  
-   現在のカルチャの規則を反映しない日付と時刻のデータ。 たとえば、月と日を表す数字ですが間違った順序で表示される可能性があります、日付の区切り記号が正しくない可能性があります。 またはタイム ゾーン情報が正しくない可能性があります。  
  
-   アプリケーションの既定のカルチャが識別されていないため、見つからないリソース。  
  
-   特定のカルチャの異常な順序で表示される文字列。  
  
-   文字列の比較または予期しない結果を返すの等価比較。  
  
 次の手順に進むことができる場合は、アプリケーションを開発するときに、グローバリゼーションの推奨事項を後に、カルチャに依存した機能が正しく、処理しを識別して発生し、テスト中にあるローカライズに関する問題を解決、 [ローカリゼーション](../../../docs/standard/globalization-localization/localization.md)です。  
  
## <a name="see-also"></a>関連項目  
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)  
 [ローカリゼーション](../../../docs/standard/globalization-localization/localization.md)  
 [グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)  
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)
