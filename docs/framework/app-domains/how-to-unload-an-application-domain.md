---
title: "方法 : アプリケーション ドメインをアンロードする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unload メソッド"
  - "アプリケーション ドメイン、アンロード"
  - "アンロード (アプリケーション ドメインの)"
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : アプリケーション ドメインをアンロードする
アプリケーション ドメインの使用を終了したら、[System.AppDomain.Unload](frlrfSystemAppDomainClassUnloadTopic) メソッドを使用してアプリケーション ドメインをアンロードします。  **Unload** メソッドは、指定したアプリケーション ドメインを正常にシャットダウンします。  アンロード プロセス中は、新たなスレッドがアプリケーション ドメインにアクセスすることはできず、アプリケーション ドメイン固有のデータ構造体はすべて解放されます。  
  
 アプリケーション ドメインに読み込まれたアセンブリは削除されるため、以後は使用できません。  アプリケーション ドメイン内のアセンブリがドメインに中立である場合、アセンブリのデータは、プロセス全体がシャットダウンされるまでメモリに残ります。  プロセス全体をシャットダウンする以外に、ドメインに中立なアセンブリをアンロードする方法はありません。  アプリケーション ドメインのアンロード要求が機能しない場合は、<xref:System.CannotUnloadAppDomainException> が生成されます。  
  
 `MyDomain` という新しいアプリケーション ドメインを作成し、所定の情報をコンソールに出力してから、アプリケーション ドメインをアンロードする例を次に示します。  このコードは、アンロードされたアプリケーション ドメインの表示名をコンソールに出力します。  このアクションによって例外が生成され、プログラムの末尾にある try ステートメントと catch ステートメントでこの例外が処理されます。  
  
## 使用例  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## 参照  
 [Programming with Application Domains](http://msdn.microsoft.com/ja-jp/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [方法 : アプリケーション ドメインを作成する](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)