---
title: "Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Visual Studio 2010 での .NET Framework 3.0 および 3.5 を対象とするプロジェクトの作成
[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を使用して、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Version 3.0 または 3.5 を対象とするプロジェクトを作成します。このトピックでは、この実行方法について説明します。  
  
> [!NOTE]
>  アクティビティを追加する際は、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の必要なバージョンが設定されていることを確認してください。アクティビティを追加した後でワークフローのターゲット バージョンを変更すると、ワークフロー検証が失敗します。  
  
> [!WARNING]
>  .Net Framework 3.5 アクティビティを持つ [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] で既存のワークフローを開くと、`this.SetValue()` でエラーが発生します。以前のバージョンの .Net Framework で作成されたプロジェクトを開くには、最初にデザイナーで空白のワークフローを開き、.Net Framework 3.5 アクティビティを追加します。  
  
## Visual Studio 2010 で .NET Framework 3.0 または 3.5 プロジェクトを作成するには  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を起動します。  
  
2.  **\[ファイル\]**、**\[新規作成\]**、**\[プロジェクト\]** の順にクリックします。  
  
3.  ダイアログ ボックス最上部のボックスで、必要なバージョンの [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を選択します。  
  
## 対象となる .NET Framework のバージョンをアップグレードするには  
  
1.  ソリューション エクスプローラーでプロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[対象のフレームワーク\]** ボックスの一覧で、必要なバージョンを選択します。