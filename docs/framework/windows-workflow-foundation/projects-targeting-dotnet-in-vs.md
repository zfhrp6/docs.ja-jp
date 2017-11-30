---
title: "Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 95348ad57bb4dce1799c1ddf741b69f0e2b969af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成
[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を使用して、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Version 3.0 または 3.5 を対象とするプロジェクトを作成します。 このトピックでは、この実行方法について説明します。  
  
> [!NOTE]
>  アクティビティを追加する際は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の必要なバージョンが設定されていることを確認してください。 アクティビティを追加した後でワークフローのターゲット バージョンを変更すると、ワークフロー検証が失敗します。  
  
> [!WARNING]
>  .Net Framework 3.5 アクティビティを持つ [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] で既存のワークフローを開くと、`this.SetValue()` でエラーが発生します。 以前のバージョンの .Net Framework で作成されたプロジェクトを開くには、最初にデザイナーで空白のワークフローを開き、.Net Framework 3.5 アクティビティを追加します。  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Visual Studio 2010 で .NET Framework 3.0 または 3.5 プロジェクトを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。  
  
2.  選択**ファイル**、**新しい**、**プロジェクト**です。  
  
3.  ダイアログ ボックス最上部のボックスで、必要なバージョンの [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を選択します。  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>対象となる .NET Framework のバージョンをアップグレードするには  
  
1.  ソリューション エクスプ ローラーでプロジェクトを右クリックし **プロパティ**です。  
  
2.  **ターゲット フレームワーク**ドロップダウン リストで、目的のバージョンを選択します。
