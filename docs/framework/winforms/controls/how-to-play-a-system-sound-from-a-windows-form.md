---
title: "方法 : Windows フォームからシステム サウンドを再生する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サウンド、システムのイベントの再生"
  - "Windows フォームのサウンドを再生"
  - "システム サウンドを再生 (Windows フォームから)"
  - "システムのサウンドを再生"
  - "SoundPlayer クラスでは、システム サウンド"
  - "サウンドの再生"
  - "サウンドの例 [Windows フォーム]"
ms.assetid: afb206ff-4824-4804-a8d4-185bf5ad8e7c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームからシステム サウンドを再生する
次のコード例の再生中、`Exclamation`実行時にシステム サウンドです。 システム サウンドの詳細については、次を参照してください。 <xref:System.Media.SystemSounds>します。  
  
## <a name="example"></a>例  
  
```vb  
Public Sub PlayExclamation()  
    SystemSounds.Exclamation.Play()  
End Sub  
  
```  
  
```csharp  
public void playExclamation()  
{  
    SystemSounds.Exclamation.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   参照、 <xref:System.Media?displayProperty=fullName>名前空間。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer>   
 <xref:System.Media.SystemSounds>   
 [方法: Windows フォームからビープ音を再生します。](../../../../docs/framework/winforms/controls/how-to-play-a-beep-from-a-windows-form.md)   
 [方法: Windows フォームからサウンドを再生](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)