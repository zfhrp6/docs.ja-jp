---
title: "Deprecated types in Windows Workflow Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Deprecated types in Windows Workflow Foundation
.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。  .NET 4.5 ベータ リリースからは、"WF 3" <xref:System.Workflow.Activities>、<xref:System.Workflow.ComponentModel>、および <xref:System.Workflow.Runtime> 名前空間に含まれる型のほとんどが、使用を推奨されない旧式扱いとなります。  
  
## 旧式の名前空間とツール  
 次のアセンブリには、今後使用を推奨されなくなるパブリック型が 1 つ以上含まれています。  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 その結果、推奨されなくなった WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます。  
  
  **警告 BC40000: X は互換性のために残されています: WF 3 の型の使用は推奨されていません。  代わりに WF 4 を使用してください。**  WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です \(4.5 では行われません\)。  この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。  もちろん、WF 3 の型は [Microsoft サポート ライフサイクル ポリシー](http://aka.ms/MicrosoftSupportLifecycle) に基づいて引き続きサポートされます。  既存の WF 3 アプリケーションは .NET 4.5 でも問題なく動作します。また、WF 3 ベースの新規および既存ソリューションは [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] でもサポートされます。  
  
 <xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。  
  
 WF 4 へのアプリケーション移行作業に役立つリソースとしては、MSDN サイトの[移行のガイドライン](http://aka.ms/WF4MigrationGuidance)に関する記事と、[WF Codeplex](http://aka.ms/WFCodeplex) サイトにある [WF 4 移行キット](http://aka.ms/WF4MigrationKit) があります。