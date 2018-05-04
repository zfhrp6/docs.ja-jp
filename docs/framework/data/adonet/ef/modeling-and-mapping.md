---
title: モデリングとマッピング
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 88c8786a5e538d8441e03e46e59743e4c489b4c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="modeling-and-mapping"></a>モデリングとマッピング
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。 Visual Studio で Entity Data Model ツールは、作成することができます。[edmx ファイル](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)データベースまたはグラフィカルなモデルと、更新データベースまたはモデルのいずれかが変更されたときにこのファイルからです。  
  
 Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。 Code First の開発に対しては、2 つの異なるシナリオがあります。 どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。  
  
 詳細については、次を参照してください。[マッピングの概念モデルの作成と](http://go.microsoft.com/fwlink/?LinkId=235016)です。  
  
 含まれている EDM のジェネレーターを使用することも、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]です。 EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。 モデルとマッピングの内容を手動で作成することもできます。 詳細については、次を参照してください。 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)です。
