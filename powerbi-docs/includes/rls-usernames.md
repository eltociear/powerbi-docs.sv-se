---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61194085"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>Använda DAX-funktionen username() eller userprincipalname()
Du kan använda funktionerna DAX *username()* eller *userprincipalname()* i din datauppsättning. Du kan använda dem i uttryck i Power BI Desktop. När du publicerar din modell kommer den att användas i Power BI-tjänsten.

I Power BI Desktop *username()* returneras en användare i formatet *domän\användare* och *userprincipalname()* returneras en användare i formatet  <em>user@contoso.com</em>.

I Power BI-tjänsten *username()* och *userprincipalname()* både returnerar användarens primära namn (User Principal Name). Detta liknar en e-postadress.

