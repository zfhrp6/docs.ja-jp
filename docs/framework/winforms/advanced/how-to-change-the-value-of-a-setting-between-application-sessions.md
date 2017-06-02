---
title: "方法 : アプリケーション セッション間で設定値を変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション設定 [Windows フォーム], アプリケーション セッション間"
  - "アプリケーション設定 [Windows フォーム], 変更"
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : アプリケーション セッション間で設定値を変更する
アプリケーションのコンパイルと配置後に、アプリケーション セッション間で設定値を変更する場合があります。  たとえば、接続文字列が適切なデータベースの場所を指すように変更します。  設計時に使用したツールは、アプリケーションをコンパイルして配置した後は使用できないので、ファイル内の設定値を手動で変更する必要があります。  
  
### アプリケーション セッション間で設定値を変更するには  
  
1.  Microsoft メモ帳などのテキスト エディターまたは XML エディターを使用して、アプリケーションに関連付けらている .config ファイルを開きます。  
  
2.  変更する設定のエントリを探します。  それは、次の例に似ています。  
  
    ```  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  新しい設定値を入力し、ファイルを保存します。  
  
## 参照  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)