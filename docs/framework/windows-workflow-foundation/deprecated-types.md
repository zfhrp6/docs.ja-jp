---
title: Windows Workflow Foundation で非推奨の型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 899d21f23c0500a1df01916d1da210b2f9bea95b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation で非推奨の型
.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。 .NET 4.5 ベータ版のリリースでは、"WF 3"で型の大部分のマークを付けるおは<xref:System.Workflow.Activities>、 <xref:System.Workflow.ComponentModel>、および<xref:System.Workflow.Runtime>不使用と名前空間。  
  
## <a name="obsolete-namespaces-and-tools"></a>旧式の名前空間とツール  
 次のアセンブリには、今後使用を推奨されなくなるパブリック型が 1 つ以上含まれています。  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   Wfc.exe  
  
 その結果、非推奨とされた WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます：  
  
 **警告 bc 40000: X が廃止されています: WF 3 の型は使用されなくなりました。代わりに WF 4 を使用してください。** WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です (4.5 では行われません)。 この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。 、当然ながら、引き続きこれら WF 3 の型をサポートするために、[マイクロソフト サポート ライフ サイクル ポリシー](http://aka.ms/MicrosoftSupportLifecycle)です。 既存の WF 3 アプリケーションは .NET 4.5 でも問題なく動作します。また、WF 3 ベースの新規および既存ソリューションは [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] でもサポートされます。  
  
 <xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。  
  
 WF 4 にアプリケーションを移行する顧客にとってはのヘルプを検索、[ワークフロー 4 移行のガイダンス](migration-guidance.md)です。
