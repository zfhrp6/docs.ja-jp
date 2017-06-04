---
title: ".NET Framework の構成ファイル スキーマ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - ".NET Framework アプリケーション構成, 構成スキーマ"
  - "app.config ファイル, スキーマ"
  - "アプリケーション構成ファイル, スキーマ"
  - "アプリケーション開発 [.NET Framework], スキーマ"
  - "構成スキーマ [.NET Framework]"
  - "構成の設定 [.NET Framework], アプリケーション"
  - "コンテナー タグ"
  - "エンタープライズ セキュリティ構成ファイル"
  - "enterprisesec.config ファイル"
  - "マシン構成ファイル"
  - "machine.config ファイル"
  - "スキーマ構成の設定"
  - "スキーマ, 構成の設定"
  - "セキュリティ [.NET Framework], 構成ファイル"
  - "security.config ファイル"
  - "整形式の XML"
  - "XML タグ"
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# .NET Framework の構成ファイル スキーマ
構成ファイルは、設定を変更し、アプリのポリシーを設定するために使用できる標準 XML ファイルです。  .NET Framework の構成スキーマは、アプリの動作を制御するために構成ファイルで使用できる要素で構成されます。  このセクションの目次は、スキーマ、起動時の階層、ランタイム、ネットワーク、およびその他の種類の構成設定を反映しています。  
  
 構成ファイルの種類、形式、および場所については、「[アプリの構成](../../../../docs/framework/configure-apps/index.md)」の記事を参照してください。  構成ファイルを直接編集するには、XML に関する知識が必要です。  
  
> [!IMPORTANT]
>  構成ファイルの XML タグおよび属性では、大文字と小文字が区別されます。  
  
## このセクションの内容  
 [\<configuration\> 要素](../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
 すべての構成ファイルの最上位要素である `<configuration>` 要素について説明します。  
  
 [\<assemblyBinding\> 要素](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)  
 構成レベルでのアセンブリ バインディング ポリシーを指定します。  
  
 [\<linkedConfiguration\> 要素](../../../../docs/framework/configure-apps/file-schema/linkedconfiguration-element.md)  
 インクルードする構成ファイルを指定します。  
  
 [スタートアップ設定スキーマ](../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 使用する共通言語ランタイムのバージョンを指定する要素について説明します。  
  
 [ランタイム設定スキーマ](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 アセンブリのバインディングとランタイムの動作を構成する要素について説明します。  
  
 [ネットワーク設定スキーマ](../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 .NET Framework がインターネットに接続する方法を指定する要素について説明します。  
  
 [暗号設定スキーマ](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる要素について説明します。  
  
 [構成セクション スキーマ](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)  
 カスタム設定の構成セクションを作成し、使用するための要素について説明します。  
  
 [トレースおよびデバッグ設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 トレース スイッチとリスナーを指定する要素について説明します。  
  
 [コンパイラおよび言語プロバイダー設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 使用できる言語プロバイダーのコンパイラの構成を指定する要素について説明します。  
  
 [アプリケーション設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)  
 Windows フォームや ASP.NET アプリケーションで、アプリケーション スコープおよびユーザー スコープの設定の格納と取得を可能にする要素について説明します。  
  
 [Web 設定スキーマ](../../../../docs/framework/configure-apps/file-schema/web/index.md)  
 IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。  aspnet.config ファイルで使用します。  
  
## 関連項目  
 [Remoting Settings Schema](http://msdn.microsoft.com/ja-jp/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)  
 リモート処理を実装するクライアント アプリケーションとサーバー アプリケーションを構成する要素について説明します。  
  
 [ASP.NET 設定スキーマ](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx)  
 ASP.NET Web アプリケーションの動作を制御する要素について説明します。  
  
 [Web Services Settings Schema](http://msdn.microsoft.com/ja-jp/f84d6d55-1add-4eb7-ae46-33df5833ea2e)  
 ASP.NET Web サービス、およびそれらのクライアントの動作を制御する要素について説明します。  
  
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/ja-jp/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 セキュリティ、アセンブリのバインディング、および .NET Framework のリモート処理を構成する方法について説明します。