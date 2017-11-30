---
title: "ローカリゼーション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a>ローカリゼーション
ローカライズは、アプリケーションのリソースをアプリケーションでサポートされる各カルチャのローカライズ版に変換するプロセスです。 完了後にのみローカライズの手順に進む必要があります、[ローカライズ化のレビュー](../../../docs/standard/globalization-localization/localizability-review.md)グローバライズされたアプリケーションがローカライズ可能であることを確認する手順。  
  
 ローカライズ可能なアプリケーションは、2 つの概念ブロック、すべてのユーザー インターフェイス要素を格納するブロックと実行可能コードを格納するブロックに分割されます。 ユーザー インターフェイス ブロックには、文字列、エラー メッセージ、ダイアログ ボックス、メニューのニュートラル カルチャについての埋め込みオブジェクト リソースなどのローカライズ可能なユーザー インターフェイス要素のみが含まれています。 コード ブロックには、サポートされているすべてのカルチャが使用するアプリケーション コードだけが含まれています。 共通言語ランタイムには、そのリソースからアプリケーションの実行可能コードを分離するサテライト アセンブリ リソース モデルがサポートしています。 このモデルの実装の詳細については、次を参照してください。[デスクトップ アプリでのリソース](../../../docs/framework/resources/index.md)です。  
  
 アプリケーションの各ローカライズ バージョンでは、ローカライズされたユーザー インターフェイス ブロックが、ターゲット カルチャに適切な言語に翻訳を含む新しいサテライト アセンブリを追加します。 すべてのカルチャのコード ブロックは同じである必要があります。 ユーザー インターフェイスを使用してブロックのコード ブロックのローカライズされたバージョンの組み合わせには、アプリケーションのローカライズされたバージョンが生成されます。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]ターゲットのカルチャに対して Windows フォームをすばやくローカライズできるようにする Windows フォーム リソース エディター (Winres.exe) を提供します。 このツールの使用方法の詳細については、次を参照してください。 [Winres.exe (Windows フォーム リソース エディター)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)です。  
  
## <a name="see-also"></a>関連項目  
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)  
 [ローカライズ化の確認](../../../docs/standard/globalization-localization/localizability-review.md)  
 [グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)  
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)
