---
title: "ローカリゼーション | Microsoft Docs"
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
  - "アプリケーション開発 [.NET Framework], ローカリゼーション"
  - "コード ブロック"
  - "カルチャ, ローカリゼーション"
  - "グローバル アプリケーション, ローカリゼーション"
  - "グローバリゼーション [.NET Framework], ローカリゼーション"
  - "国際対応のアプリケーション [.NET Framework], ローカリゼーション"
  - "ローカリゼーション [.NET Framework], ローカリゼーションの概要"
  - "ローカライズ (リソースを)"
  - "ユーザー インターフェイス ブロック"
  - "国際対応アプリケーション, ローカリゼーション"
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# ローカリゼーション
ローカリゼーションとは、アプリケーションのリソースを、アプリケーションでサポートする各カルチャのローカライズ バージョンへ翻訳する作業です。  [ローカライズ化の確認](../../../docs/standard/globalization-localization/localizability-review.md) ステップで、グローバライズ済みアプリケーションがローカライズ可能であることを確認してから、ローカリゼーションを開始してください。  
  
 ローカライズ可能なアプリケーションは、すべてのユーザー インターフェイス要素が格納されているブロックと、実行可能コードが格納されているブロックに分かれています。  ユーザー インターフェイス ブロックには、ニュートラル カルチャのローカライズ可能ユーザー インターフェイス要素 \(文字列、エラー メッセージ、ダイアログ ボックス、メニュー、埋め込みオブジェクト リソースなど\) だけが格納されています。  コード ブロックには、サポートされるすべてのカルチャで使用されるアプリケーション コードだけが格納されています。  共通言語ランタイムでサポートされているサテライト アセンブリ リソース モデルでは、アプリケーションの実行可能コードとリソースが分離されます。  このモデルの実装方法の詳細については、「[デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)」を参照してください。  
  
 アプリケーションのローカライズ バージョンごとに、サテライト アセンブリを追加します。このアセンブリには、対象カルチャの適切な言語に翻訳されたローカライズ済みユーザー インターフェイス ブロックが格納されます。  コード ブロックは、すべてのカルチャで同一です。  ユーザー インターフェイス ブロックのローカライズ バージョンとコード ブロックの組み合わせにより、アプリケーションのローカライズ バージョンが実現します。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] に収録されている Windows フォーム リソース エディター \(Winres.exe\) を使用すると、Windows フォームを対象カルチャに合わせて簡単にローカライズできます。  このツールの使用方法については、「[Winres.exe \(Windows フォーム リソース エディター\)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)」を参照してください。  
  
## 参照  
 [グローバライズとローカライズ](../../../docs/standard/globalization-localization/index.md)   
 [ローカライズ化の確認](../../../docs/standard/globalization-localization/localizability-review.md)   
 [グローバリゼーション](../../../docs/standard/globalization-localization/globalization.md)   
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)