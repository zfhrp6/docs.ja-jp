---
title: "方法: .NET Framework で基本的な文字列操作を実行する | Microsoft Docs"
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
  - "文字列 [.NET Framework], 例"
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法: .NET Framework で基本的な文字列操作を実行する
「[基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)」で説明したいくつかのメソッドを使用して、実際のアプリケーションで行われるような文字列操作を行うクラスを作成する例を次に示します。  `MailToData` クラスは個人の名前と住所を別々のプロパティに格納し、`City`、`State`、`Zip` の各フィールドを連結して 1 つの文字列としてユーザーに表示できるようにします。  さらに、このクラスを使用すると、ユーザーは都市、州、郵便番号を 1 つの文字列として入力でき、アプリケーションがその文字列を自動的に解析し、対応するプロパティに正しい情報を入力します。  
  
 わかりやすくするために、この例ではコマンド ライン インターフェイスを持つコンソール アプリケーションを使用します。  
  
## 使用例  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 上のコードを実行すると、ユーザーは名前と住所を入力するように要求されます。  アプリケーションは入力された情報を適切なプロパティに格納し、都市、州、郵便番号の各情報をまとめて表示する 1 つの文字列を作成して、ユーザーに対して表示します。  
  
## 参照  
 [基本的な文字列操作](../../../docs/standard/base-types/basic-string-operations.md)