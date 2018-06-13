---
title: 継承のサポート
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 3d396632902b178eee34801a9716d8aa222a08d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359563"
---
# <a name="inheritance-support"></a>継承のサポート
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] サポートしている*シングル テーブル マッピング*です。 これは、1 つの継承階層全体が単一のデータベース テーブルに保存されることを意味します。 テーブルには、階層構造内で使用され得るすべてのデータ列の平坦化された共用体が格納されます  (2 つのテーブルを 1 つに結合し、元のテーブルのいずれかにあった行が新しいテーブルに含まれるようにした結果、1 つの共用体が形成されます)。行によって表されるインスタンスの型に適合しない列には null が設定されます。  
  
 シングル テーブル マッピング形式は、継承を表す最も単純な形式であり、多くのクエリのカテゴリで良好なパフォーマンス特性を示します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でこのマッピングを実装するには、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 詳細については、次を参照してください。[する方法: 継承階層をマップ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)です。  
  
 Visual Studio を使用している開発者が使用することも、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]継承階層をマップします。  
  
## <a name="see-also"></a>関連項目  
 [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
