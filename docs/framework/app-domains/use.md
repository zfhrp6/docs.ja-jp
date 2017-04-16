---
title: "アプリケーション ドメインの使用 | Microsoft Docs"
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
  - "アプリケーション ドメイン、バージョン情報"
  - "共通言語ランタイム、アプリケーション ドメイン"
  - "ランタイム、アプリケーション ドメイン"
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# アプリケーション ドメインの使用
アプリケーション ドメインは、共通言語ランタイムで使用する分離の単位です。  アプリケーション ドメインは、プロセスの内部で作成および実行します。  通常、アプリケーション ドメインはランタイム ホストによって作成されます。ランタイム ホストはアプリケーションの一種で、ランタイムをプロセスに読み込み、アプリケーション ドメイン内でユーザー コードを実行します。  ランタイム ホストは、プロセスと既定のアプリケーション ドメインを作成し、アプリケーション ドメイン内でマネージ コードを実行します。  ランタイム ホストには ASP.NET、Microsoft Internet Explorer、Windows シェルがあります。  
  
 ほとんどのアプリケーションでは、ランタイム ホストが必要なアプリケーション ドメインをすべて作成するため、独自のアプリケーション ドメインを作成する必要はありません。  ただし、アプリケーションでコードを分離する、または DLL を使用したりアンロードしたりする必要がある場合は、追加のアプリケーション ドメインを作成して構成できます。  
  
## このセクションの内容  
 [方法 : アプリケーション ドメインを作成する](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 アプリケーション ドメインをプログラムで作成する方法を説明します。  
  
 [方法 : アプリケーション ドメインをアンロードする](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 アプリケーション ドメインをプログラムでアンロードする方法を説明します。  
  
 [方法 : アプリケーション ドメインを構成する](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 アプリケーション ドメインの構成の概要を説明します。  
  
 [アプリケーション ドメインからのセットアップ情報の取得](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 アプリケーション ドメインからセットアップ情報を取得する方法を説明します。  
  
 [方法 : アプリケーション ドメインにアセンブリを読み込む](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 アプリケーション ドメインにアセンブリを読み込む方法を説明します。  
  
 [方法 : アセンブリから型およびメンバーの情報を取得する](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 アセンブリに関する情報を取得する方法を説明します。  
  
 [アセンブリのシャドウ コピー](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 シャドウ コピーによる使用中のアセンブリの更新、およびシャドウ コピーを設定する方法を説明します。  
  
 [方法: 初回例外通知を受け取る](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 共通言語ランタイムが例外ハンドラーの検索を開始する前に、例外がスローされたことを知らせる通知を受け取る方法について説明します。  
  
 [アセンブリ読み込みの解決](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを使用してアセンブリの読み込みの失敗を解決する方法について説明します。  
  
## 関連項目  
 <xref:System.AppDomain>  
 アプリケーション ドメインを表します。  アプリケーション ドメインを作成および制御するためのメソッドを提供します。  
  
## 関連項目  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 アセンブリの機能について概要を説明します。  
  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 アセンブリを作成し、署名し、その属性を設定する方法を説明します。  
  
 [動的メソッドおよびアセンブリの出力](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 動的アセンブリの作成方法を説明します。  
  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインの概念的な概要を説明します。  
  
 [リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)  
 **Reflection** クラスを使って、アセンブリに関する情報を取得する方法を説明します。