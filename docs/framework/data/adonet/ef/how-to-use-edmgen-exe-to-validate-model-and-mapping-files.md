---
title: '方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する'
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: 197af6ae86de4057b864ef211c36f19aad83b003
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755800"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a>方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する
このトピックの内容を使用する方法を示しています、 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)モデルおよびマッピング ファイルを検証するツールです。 詳細については、次を参照してください。 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)です。  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a>EdmGen.exe を使用して School モデルを検証するには  
  
1.  School データベースを作成します。 詳細については、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)です。  
  
2.  School モデルを生成します。 詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。  
  
3.  コマンド プロンプトで、次のコマンド (改行なし) を実行します。  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a>関連項目  
 [方法: Entity Framework プロジェクトを手動で構成します。](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [方法: クエリのパフォーマンスを向上させるためにビューの事前生成](http://msdn.microsoft.com/library/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
