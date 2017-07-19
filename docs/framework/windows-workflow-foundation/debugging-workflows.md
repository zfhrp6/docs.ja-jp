---
title: "デバッグのワークフロー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# デバッグのワークフロー
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。  ワークフローは、デザイナー、XAML、およびコードでデバッグできます。  
  
## ワークフロー デザイナーでのデバッグ  
 ワークフロー デザイナーでブレークポイントをアクティビティに設定するには、アクティビティを選択して **F9** キーを押すか、アクティビティのコンテキスト メニューを使用します。  ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。  次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]「[ワークフロー デザイナーを使用したワークフローのデバッグ](../Topic/Debugging%20Workflows%20with%20the%20Workflow%20Designer.md)」  
  
## XAML でのデバッグ  
 デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。  XAML で実行ポイントを表示するには、ワークフローの実行が一時停止したときにワークフロー デザイナーで **\[XAML ビュー\]** を選択します。  デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]「[ワークフロー デザイナーを使用して XAML をデバッグする方法](../Topic/How%20to:%20Debug%20XAML%20with%20the%20Workflow%20Designer.md)」  
  
## コードでのデバッグ  
 コードのブレークポイントは、他の命令型アプリケーションで使用する方法と同様に [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で使用できます。  コード ペインの左側の余白をクリックし、コードのブレークポイントを作成するか、**F9** キーを押してカーソル位置にブレークポイントを配置します。  
  
## ワークフロー プロセスへのアタッチ  
 ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。  そのため、ワークフロー作成者は、Internet Information Services \(IIS\) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。  
  
## リモート デバッグ  
 [!INCLUDE[wf](../../../includes/wf-md.md)] のリモート デバッグは、他の [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] コンポーネントのリモート デバッグと同じように機能します。  リモート デバッグの使用については、「[方法: リモート デバッグを有効にする](http://go.microsoft.com/fwlink/?LinkId=196257)」を参照してください。  
  
> [!NOTE]
>  ワークフロー アプリケーションが x86 アーキテクチャを対象とし、64 ビットのオペレーティング システムを実行しているコンピューターでホストされる場合は、リモート デバッグは、[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] をリモート コンピューターにインストールするか、またはワークフロー アプリケーションの対象が **Any CPU** に変更されなければ機能しません。  
  
## ワークフロー デバッグ サービスの拡張  
 ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]「<xref:System.Activities.Presentation.Debug.DebuggerService>」のトピックを参照してください。