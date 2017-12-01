---
title: "方法: .NET Framework で基本的な文字列操作を実行する"
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
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>方法: .NET での基本的な文字列操作の実行
次の例で説明した手法のいくつか、[基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)実際のアプリケーションで見つかる可能性があるように文字列操作を実行するクラスを構築するためにトピックです。 `MailToData` クラスは、個人の名前とアドレスを個別のプロパティに格納し、`City`、`State`、`Zip` フィールドを組み合わせて、ユーザーに表示する1 つの文字列にする方法を提供します。 さらに、このクラスを使用して、ユーザーが市区町村、都道府県、および郵便番号情報を 1 つの文字列として入力することができます。アプリケーションは自動的に 1 つの文字列を解析し、対応するプロパティに適切な情報を入力します。  
  
 わかりやすいように、この例ではコマンド ライン インターフェイスによるコンソール アプリケーションを使用します。  
  
## <a name="example"></a>例  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 上記のコードを実行すると、ユーザーは自分の名前とアドレスを入力するように求められます。 アプリケーションは、適切なプロパティに情報を格納し、市区町村、都道府県、および郵便番号情報を表示する 1 つの文字列を作成して、ユーザーに情報を表示します。  
  
## <a name="see-also"></a>関連項目  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)
