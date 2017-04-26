---
title: ".NET Framework の開発ガイド | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, development guide
ms.assetid: 26e3d285-24c3-435c-a797-9fe5affb8525
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: b630f2dc91068168b1d57b37ad80d79f5e3d1738
ms.openlocfilehash: 88219e428409a71eb2706c97dca31ccde38bb918
ms.lasthandoff: 04/18/2017

---
# <a name="net-framework-development-guide"></a>.NET Framework の開発ガイド
ここでは、.NET Framework アプリの作成、構成、デバッグ、保護、および配置を行う方法について説明します。 また、動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理などの技術領域に関する情報も提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アプリケーションの基本事項](../../docs/standard/application-essentials.md)  
 アプリ ドメインとアセンブリを利用したプログラミング、属性の使用、基本型の書式指定と解析、コレクションの使用、イベントおよび例外の処理、ファイルおよびデータ ストリームの使用、ジェネリックの使用など、基本的なアプリ開発タスクについて説明します。  
  
 [データとモデリング](../../docs/framework/data/index.md)  
 ADO.NET、統合言語クエリ (LINQ: Language-Integrated Query)、WCF Data Services、および XML を使用してデータにアクセスする方法について説明します。  
  
 [クライアント アプリケーション](../../docs/framework/develop-client-apps.md)  
 Windows Presentation Foundation (WPF) または Windows フォームを使用して Windows ベースのアプリを作成する方法について説明します。  
  
 [ASP.NET を使用した Web アプリケーション](../../docs/framework/develop-web-apps-with-aspnet.md)  
 ASP.NET を使用して最小限のコーディングでエンタープライズ クラスの Web アプリケーションを構築する方法に関する情報へのリンクを示します。  
  
 [WCF を使用したサービス指向アプリケーション](../../docs/framework/wcf/index.md)  
 Windows Communication Foundation (WCF) を使用して、安全で信頼できるサービス指向のアプリを構築する方法について説明します。  
  
 [Windows Workflow Foundation でワークフローを構築する](windows-workflow-foundation/index.md)     
 Windows Workflow Foundation (WF) を使用するためのプログラミング モデル、サンプル、およびツールについて説明します。   

 [Windows サービス アプリケーション](../../docs/framework/windows-services/index.md)  
 Visual Studio および .NET Framework を使用して、サービスとしてインストールされるアプリを作成し、その動作を開始、停止、制御する方法について説明します。  
  
 [並列処理と同時実行](../../docs/standard/parallel-processing-and-concurrency.md)  
 マネージ スレッド処理、並列プログラミング、および非同期プログラミングのデザイン パターンについて説明します。  
  
 [.NET Framework のネットワーク プログラミング](../../docs/framework/network-programming/index.md)  
 アプリにすばやく簡単に統合できる、複数層の拡張可能なインターネット サービスのマネージ実装について説明します。  
  
 [.NET Framework アプリの構成](configure-apps/index.md)    
 構成ファイルを使用して、.NET Framework アプリを再コンパイルすることなく設定を変更する方法を説明します。  
  
 [.NET ネイティブによるアプリのコンパイル](../../docs/framework/net-native/index.md)  
 [!INCLUDE[net_native](../../includes/net-native-md.md)] プリコンパイル テクノロジを使用して、Windows ストア アプリをビルドおよび配置する方法について説明します。 [!INCLUDE[net_native](../../includes/net-native-md.md)] は、マネージ コード (C#) で記述され、.NET Framework を対象とするアプリをネイティブ コードにコンパイルします。  
  
 [セキュリティ](../../docs/standard/security/index.md)  
 .NET Framework において安全なアプリの開発を促進するクラスおよびサービスに関する情報を示します。  
  
 [デバッグ、トレース、およびプロファイリング](../../docs/framework/debug-trace-profile/index.md)  
 .NET Framework アプリとアプリ環境のテスト、最適化、およびプロファイリングを行う方法について説明します。 開発者向けの情報だけでなく、管理者向けの情報も記載されています。  
  
 [複数のプラットフォームの開発](../../docs/standard/cross-platform/index.md)  
 .NET Framework を使用して複数のプラットフォームおよび複数のデバイス (電話、デスクトップ、Web など) で共有できるアセンブリを作成する方法に関する情報を示します。  
  
 [配置](../../docs/framework/deployment/index.md)  
 .NET Framework アプリをパッケージ化して配布する方法を説明します。開発者および管理者向けの配置ガイドも含まれています。  
  
 [パフォーマンス](../../docs/framework/performance/index.md)  
 キャッシュ、遅延初期化、信頼性、および ETW イベントについて説明します。  
  
 <!--zz [Advanced Reading for the .NET Framework](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)  
 Provides information about advanced development tasks and techniques in the .NET Framework, including extensibility, interoperability, and reflection. Also includes the reference topics for unmanaged APIs that can be used by managed apps, such as runtime hosts, compilers, disassemblers, debuggers, and profilers.  --> 
  
## <a name="reference"></a>参照  
 [.NET Framework クラス ライブラリ](https://docs.microsoft.com/en-us/dotnet/api/?view=netframework-4.7)  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の名前空間に含まれる各クラスの構文、コード例、および使用情報を示します。  
  
## <a name="related-sections"></a>関連項目  
 [はじめに](../../docs/framework/get-started/index.md)  
 .NET Framework の包括的な概要と、追加リソースへのリンクを説明します。  
  
 [新機能](../../docs/framework/whats-new/index.md)  
 最新バージョンの .NET Framework の主要な新機能と変更点について説明します。 新旧の型とメンバーのリストを含み、.NET Framework の以前のバージョンからアプリを移行する方法について説明します。  
  
 [ツール](../../docs/framework/tools/index.md)  
 .NET Framework テクノロジを使ってアプリを開発、構成、配置するのに役立つツールについて説明します。  
  
 [.NET Framework のサンプル](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)  
 .NET Framework のテクノロジを紹介するサンプル アプリを参照できる MSDN コード サンプル ギャラリーへのリンクです。
