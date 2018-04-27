---
title: デバッグのワークフロー
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 866fe3ebcec295b57444f937b3b6fd6677bfe0f4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="debugging-workflows"></a>デバッグのワークフロー
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。 ワークフローは、デザイナー、XAML、およびコードでデバッグできます。  
  
## <a name="debugging-in-the-workflow-designer"></a>ワークフロー デザイナーでのデバッグ  
 アクティビティを強調表示し、キーを押して、ワークフロー デザイナーでアクティビティにブレークポイントを設定することができます**F9**アクティビティのコンテキスト メニューを使用します。 ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。 次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [ワークフロー デザイナーにワークフローのデバッグ](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)です。  
  
## <a name="debugging-in-xaml"></a>XAML でのデバッグ  
 デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。 XAML での実行ポイントを表示する選択**XAML ビュー**ワークフローの実行が一時停止すると、ワークフロー デザイナーでします。 デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [方法: ワークフロー デザイナーで XAML をデバッグ](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)です。  
  
## <a name="debugging-in-code"></a>コードでのデバッグ  
 コードのブレークポイントは、他の命令型アプリケーションで使用する方法と同様に [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で使用できます。 コードのブレークポイントを作成するコード ペインの左マージンをクリックしてまたはキーを押して**F9**カーソル位置にブレークポイントを配置します。  
  
## <a name="attaching-to-a-workflow-process"></a>ワークフロー プロセスへのアタッチ  
 ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。 そのため、ワークフロー作成者は、Internet Information Services (IIS) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。  
  
## <a name="remote-debugging"></a>Remote Debugging  
 Windows Workflow Foundation (WF) のリモート デバッグと、その他の Visual Studio コンポーネントのリモート デバッグと同様に機能します。 リモート デバッグの使用方法の詳細については、次を参照してください。[する方法: リモート デバッグを有効にする](http://go.microsoft.com/fwlink/?LinkId=196257)です。  
  
> [!NOTE]
>  ワークフロー アプリケーションが x86 を対象とする場合のアーキテクチャが、64 ビットのオペレーティング システムを実行するコンピューターでホストされているリモート デバッグが機能しません、リモート コンピューターで Visual Studio がインストールされているかに、ワークフロー アプリケーションのターゲットを変更しない限り、**任意の CPU**です。  
  
## <a name="extending-the-workflow-debugging-service"></a>ワークフロー デバッグ サービスの拡張  
 ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]「<xref:System.Activities.Presentation.Debug.DebuggerService>」のトピックを参照してください。
