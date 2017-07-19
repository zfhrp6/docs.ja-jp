---
title: "Windows フォームのセキュリティ | Microsoft Docs"
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
  - "アクセス制御, Windows フォーム"
  - "デザイナーのアクセスのセキュリティ"
  - "アクセス許可, Windows フォーム"
  - "セキュリティ [Windows フォーム]"
  - "セキュリティ ポリシー, Windows フォーム"
  - "Windows フォーム, セキュリティ"
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows フォームのセキュリティ
Windows フォームには、コード ベースのセキュリティ モデルが使用されています。コードを実行するユーザーに関係なく、セキュリティ レベルはコードに対して設定されます。  これは、コンピューター システム上に既に用意されている任意のセキュリティ スキーマに追加して使用されます。  既に用意されているセキュリティ スキーマには、ブラウザーのセキュリティ スキーマ \(Internet Explorer で使用されるゾーン ベースのセキュリティなど\) とオペレーティング システムのセキュリティ スキーマ \(Windows NT の資格情報ベースのセキュリティなど\) があります。  
  
## このセクションの内容  
 [Windows フォームのセキュリティの概要](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 .NET Framework のセキュリティ モデルについて簡単に説明し、アプリケーション内の Windows フォームの安全性を確保するための基本的な手順を示します。  
  
 [Windows フォームにおけるファイルおよびデータへのより安全なアクセス](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 やや信頼度の低い環境でファイルとデータにアクセスする方法について説明します。  
  
 [Windows フォームでのより安全な印刷](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 やや信頼度の低い環境で印刷機能にアクセスする方法について説明します。  
  
 [Windows フォームのセキュリティに関するその他の考慮事項](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 信頼度の低い環境におけるウィンドウ操作の実行、クリップボードの使用、およびアンマネージ コードの呼び出しについて説明します。  
  
## 関連項目  
 [NIB: Default Security Policy](http://msdn.microsoft.com/ja-jp/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 Full Trust、Local Intranet、および Internet の各アクセス許可セットで許可される既定のアクセス許可の一覧を示します。  
  
 [NIB: General Security Policy Administration](http://msdn.microsoft.com/ja-jp/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 .NET Framework のセキュリティ ポリシーの管理、およびアクセス許可の度合いを高める方法について説明します。  
  
 [危険なアクセス許可とポリシー管理](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 セキュリティ システムが回避される可能性のある .NET Framework のアクセス許可の例について説明します。  
  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)  
 .NET Framework に対して安全なコードを記述するために推奨される方法を説明したトピックへのリンクを提供します。  
  
 [NIB: Requesting Permissions](http://msdn.microsoft.com/ja-jp/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 コードの実行に必要なアクセス許可をランタイムに通知するために属性を使用する方法を説明します。  
  
 [セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)  
 コードのセキュリティに関する基本的な事項を説明したトピックへのリンクを提供します。  
  
 [コード アクセス セキュリティの基礎](../../../docs/framework/misc/code-access-security-basics.md)  
 .NET Framework の実行時セキュリティ ポリシーを使用するための基本的な事項について説明します。  
  
 [NIB: Determining When to Modify Security Policy](http://msdn.microsoft.com/ja-jp/af749b17-e461-409d-84b9-a3d44789db16)  
 アプリケーションが既定のセキュリティ ポリシーから逸脱する必要がある場合の判断の方法について説明します。  
  
 [NIB: Deploying Security Policy](http://msdn.microsoft.com/ja-jp/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 セキュリティ ポリシーの変更を配置するための推奨される方法について説明します。