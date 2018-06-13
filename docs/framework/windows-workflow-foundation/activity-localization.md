---
title: アクティビティのローカライズ
ms.date: 03/30/2017
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
ms.openlocfilehash: 23a6d5c2ed202f030397eb70382896468a68a724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512464"
---
# <a name="activity-localization"></a>アクティビティのローカライズ
ワークフロー アプリケーションとコンポーネントが他のカルチャおよび言語にローカライズされる可能性がある場合は、再コンパイルせずにローカライズできるようにリソース文字列を使用する必要があります。  
  
## <a name="activity-localization"></a>アクティビティのローカライズ  
 ローカライズが必要なすべてのアプリケーション (言語とカルチャが異なり、異なるバージョンでリリースされたアプリケーション) について、ユーザーに表示される文字列は、コードに直接記述せず、リソース ファイルに格納する必要があります。 文字列を介してアクセス<!--zz <xref:System.Environment.GetResourceString> -->`GetResourceString`です。 複数の言語で配布されるコンポーネントを開発する場合、アクティビティの検証メッセージ、ユーザー定義の追跡データ、追跡メッセージ、およびエラー メッセージにもリソース文字列を使用できます。  
  
 次の演習では、リソース ファイルの使用手順を示します。  
  
#### <a name="using-resource-files-for-localized-strings"></a>ローカライズ文字列へのリソース ファイルの使用  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]でプロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加しています.**、**新しい項目の追加**.  
  
2.  選択**リソース ファイル**ErrorResources.resx というファイル名を入力します。 **[追加]** をクリックします。  
  
3.  リソース ファイルを開きます。 新しいエントリを追加、**名前**が ErrorString と**値**の「アクティビティが正しくありません」。  
  
4.  次の `using` ステートメントをクラスに追加します。  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  プロジェクトでリソース マネージャーを作成します。  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  必要に応じてリソース マネージャーから文字列を取得します。  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 次のコードは、<xref:System.Activities.Activity.CacheMetadata%2A> メソッドでローカライズした文字列を利用する方法の例です。  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
