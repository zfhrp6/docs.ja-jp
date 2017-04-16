---
title: "アクティビティのローカライズ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# アクティビティのローカライズ
ワークフロー アプリケーションとコンポーネントが他のカルチャおよび言語にローカライズされる可能性がある場合は、再コンパイルせずにローカライズできるようにリソース文字列を使用する必要があります。  
  
## アクティビティのローカライズ  
 ローカライズが必要なすべてのアプリケーション \(言語とカルチャが異なり、異なるバージョンでリリースされたアプリケーション\) について、ユーザーに表示される文字列は、コードに直接記述せず、リソース ファイルに格納する必要があります。文字列には、<xref:System.Environment.GetResourceString> を介してアクセスできます。複数の言語で配布されるコンポーネントを開発する場合、アクティビティの検証メッセージ、ユーザー定義の追跡データ、追跡メッセージ、およびエラー メッセージにもリソース文字列を使用できます。  
  
 次の演習では、リソース ファイルの使用手順を示します。  
  
#### ローカライズ文字列へのリソース ファイルの使用  
  
1.  [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] の**ソリューション エクスプローラー**でプロジェクトを右クリックし、**\[追加\]** の **\[新しい項目\]** をクリックします。  
  
2.  **\[リソース ファイル\]** を選択し、ファイルに ErrorResources.resx という名前を付けます。**\[追加\]** をクリックします。  
  
3.  リソース ファイルを開きます。**\[名前\]** が ErrorString で **\[値\]** が "The activity is not valid." の新しいエントリを追加します。  
  
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