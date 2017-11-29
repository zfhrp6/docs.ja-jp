---
title: "方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 741da2e7f69d5f8fa54f07046d88fec9cf722dbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する
このトピックでは、EDM ジェネレーター (EdmGen.exe) ツールを使用して、School データベースに基づく次のファイルを生成する方法について説明します。  
  
-   概念モデル (.csdl ファイル)  
  
-   ストレージ モデル (.ssdl ファイル)  
  
-   概念モデルとストレージ モデル間のマッピング (.msl ファイル)  
  
-   Visual Basic または C# のオブジェクト レイヤー コード  
  
-   ビュー ファイル  
  
 EdmGen.exe ツールでは、/mode:FullGeneration を使用して上記のファイルを生成します。 EdmGen.exe コマンドの詳細については、次を参照してください。 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)です。  
  
 EdmGen.exe を使用してモデル ファイルとマッピング ファイルを生成する場合は、[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] を使用するように [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロジェクトを構成する必要もあります。 詳細については、次を参照してください。[する方法: Entity Framework プロジェクトを手動で構成](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)です。  
  
> [!NOTE]
>  EdmGen.exe によって生成された概念モデルには、データベース内のすべてのオブジェクトが含まれています。 特定のオブジェクトだけを含んだ概念モデルを生成する場合は、Entity Data Model ウィザードを使用してください。 詳細については、次を参照してください。[する方法: Entity Data Model ウィザードを使用して](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)です。  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>EdmGen.exe を使用して Visual Basic プロジェクト用の School モデルを生成するには  
  
1.  School データベースを作成します。 詳細については、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)です。  
  
2.  コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>EdmGen.exe を使用して C# プロジェクト用の School モデルを生成するには  
  
1.  School データベースを作成します。 詳細については、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)です。  
  
2.  コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>関連項目  
 [モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [方法: Entity Framework プロジェクトを手動で構成します。](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [方法: クエリのパフォーマンスを向上させるためにビューの事前生成](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証するには](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
