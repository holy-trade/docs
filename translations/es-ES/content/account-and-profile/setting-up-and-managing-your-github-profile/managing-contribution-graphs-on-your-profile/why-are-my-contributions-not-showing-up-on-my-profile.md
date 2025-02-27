---
title: ¿Por qué mis contribuciones no aparecen en mi perfil?
intro: Aprende sobre las razones habituales por las cuales podrían faltar contribuciones en tu gráfica.
redirect_from:
  - /articles/why-are-my-contributions-not-showing-up-on-my-profile
  - /github/setting-up-and-managing-your-github-profile/why-are-my-contributions-not-showing-up-on-my-profile
  - /github/setting-up-and-managing-your-github-profile/managing-contribution-graphs-on-your-profile/why-are-my-contributions-not-showing-up-on-my-profile
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Profiles
shortTitle: Contribuciones faltantes
---

## Acerca de tu gráfica de contribuciones

La gráfica de contribuciones en tu perfil es un registro de las contribuciones que has hecho en los repositorios {% ifversion ghae %}que le pertenecen{% else %}de{% endif %} {% data variables.product.product_location %}. Las contribuciones son registros horarios de acuerdo a la zona horaria universal coordinada (UTC) en lugar de tu zona horaria local. Las contribuciones solo se cuentan si cumplen con determinados criterios. En algunos casos, necesitamos reconstruir tu gráfico para que aparezcan las contribuciones.

If you are part of an organization that uses SAML single sign-on (SSO), you won’t be able to see contribution activity from the organization on your profile if you do not have an active SSO session. People viewing your profile from outside your organization will see anonymized contribution activity of your contribution activity for your organization.

## Contribuciones que se cuentan

### Propuestas, solicitudes de cambios y debates

Las propuestas, solicitudes de cambios y debates aparecerán en tu gráfica de contribuciones si se abrieron en un repositorio independiente y no en una bifurcación.

### Confirmaciones
Las confirmaciones aparecerán en tu gráfico de contribución si cumplen **todas** las condiciones a continuación:
- La dirección de correo electrónico que se utiliza para las confirmaciones se asocia con tu cuenta de {% data variables.product.product_location %}.
- Las confirmaciones se hicieron en un repositorio independiente, no en una bifurcación.
- Las confirmaciones se hicieron:
  - En la rama predeterminada del repositorio
  - En la rama `gh-pages` (para los repositorios con sitios de proyecto)

Para obtener más información sobre los sitios de proyecto, consulta la sección "[Acerca de las {% data variables.product.prodname_pages %}](/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites)".

Asimismo, **al menos una** de las siguientes afirmaciones debe ser verdadera:
- Eres un colaborador en el repositorio o eres miembro de la organización a la que pertenece el repositorio.
- Has bifurcado el repositorio.
- Has abierto una solicitud de extracción o una propuesta en el repositorio.
- Has destacado el repositorio.

## Razones comunes por las que las contribuciones no se cuentan

{% data reusables.pull_requests.pull_request_merges_and_contributions %}

### La confirmación se hizo hace menos de 24 horas

Después de hacer una confirmación que cumpla con los requisitos para contar como una contribución, es posible que debas esperar hasta 24 horas para que aparezca la contribución en tu gráfico de contribución.

### Tu correo electrónico de confirmaciones de Git no está conectado a tu cuenta

Las confirmaciones deben realizase con una dirección de correo electrónico que se encuentre conectada a tu cuenta de {% data variables.product.product_location %}{% ifversion fpt or ghec %} o con la dirección de tipo `noreply` que te proporcionó {% data variables.product.prodname_dotcom %} en tus ajustes de correo electrónico{% endif %} para que pueda aparecer en tu gráfica de contribuciones.{% ifversion fpt or ghec %} Para obtener más información sobre las direcciones de correo electrónico de tipo `noreply`, consulta la sección "[Configurar tu dirección de correo electrónico para confirmaciones](/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#about-commit-email-addresses)".{% endif %}

Puedes verificar la dirección de correo electrónico para una confirmación si agregas `.patch` al final de la URL de la confirmación, por ejemplo <a href="https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch" data-proofer-ignore>https://github.com/octocat/octocat.github.io/commit/67c0afc1da354d8571f51b6f0af8f2794117fd10.patch</a>:

```
From 67c0afc1da354d8571f51b6f0af8f2794117fd10 Mon Sep 17 00:00:00 2001
From: The Octocat <octocat@nowhere.com>
Date: Sun, 27 Apr 2014 15:36:39 +0530
Subject: [PATCH] índice actualizado para un mejor mensaje de bienvenida
```

La dirección de correo electrónico en el campo `From: (Desde:)` es la dirección que se estableció en los [parámetros de configuración de Git local](/articles/set-up-git). En este ejemplo, la dirección de correo electrónico que se usó para la confirmación es `octocat@nowhere.com`.

Si la dirección de correo electrónico que se utiliza para la confirmación no está conectada a tu cuenta en {% data variables.product.product_location %}, {% ifversion ghae %}cambia aquella que se utiliza para crear confirmaciones en Git. Para obtener más información, consulta la sección "[Configurar tu dirección de correo electrónico para confirmaciones](/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#setting-your-commit-email-address-in-git)".{% else %}debes [agregar la dirección de correo electrónico](/articles/adding-an-email-address-to-your-github-account) a tu cuenta en {% data variables.product.product_location %}. Tu gráfica de contribuciones se reconstruirá automáticamente cuando agregues la nueva dirección.{% endif %}

{% warning %}

**Advertencia**: Las direcciones de correo electrónico genéricas, tales como `jane@computer.local`, no pueden agregarse a las cuentas de {% data variables.product.prodname_dotcom %}. Si usas un correo electrónico de ese estilo para tus confirmaciones, las confirmaciones no se vincularán a tu perfil {% data variables.product.prodname_dotcom %} y no aparecerán en tu gráfico de contribución.

{% endwarning %}

### La confirmación no se hizo en la rama predeterminada o en la rama `gh-pages`

Las confirmaciones solo se cuentan si se realizan en la rama predeterminada o en la rama `gh-pages` (para los repositorios con sitios de proyecto). Para obtener más información, consulta la sección "[Acerca de {% data variables.product.prodname_pages %}](/pages/getting-started-with-github-pages/about-github-pages#types-of-github-pages-sites)".

Si tus confirmaciones están en una rama que no es una rama predeterminada ni es la rama `gh-pages` y te gustaría que contaran para tus contribuciones, necesitarás realizar las siguientes acciones:
- [Abre una solicitud de extracción](/articles/creating-a-pull-request) para obtener la fusión de tus cambios en la rama predeterminada o la rama `gh-pages`.
- [Cambia la rama predeterminada](/github/administering-a-repository/changing-the-default-branch) del repositorio.

{% warning %}

**Advertencia**: El cambiar la rama predeterminada del repositorio la cambiará para todos los colaboradores de este. Realiza esta acción solamente si quieres que la nueva rama se convierta en la base respecto de todas las confirmaciones y las solicitudes de extracción que se harán en el futuro.

{% endwarning %}

### La confirmación se hizo en una bifurcación

Las confirmaciones que se hicieron en una bifurcación no contarán para tus contribuciones. Para hacer que cuenten, debes realizar una de las siguientes acciones:
- [Abre una solicitud de extracción](/articles/creating-a-pull-request) para que se fusionen tus cambios en el repositorio padre.
- Para desconectar la bifurcación y convertirla en un repositorio independiente en {% data variables.product.product_location %}, contacta a {% data variables.contact.contact_support %}. Si la bifurcación tiene a su vez más bifurcaciones, indícale al {% data variables.contact.contact_support %} si éstas deberán moverse junto con tu repositorio a una nueva red o permanecer en la actual. Para obtener más información, consulta "[Acerca de las bifurcaciones](/articles/about-forks/)."

## Leer más

- "[Divulgar u ocultar tus contribuciones privadas en tu perfil](/articles/publicizing-or-hiding-your-private-contributions-on-your-profile)"
- "[Ver las contribuciones en tu página de perfil](/articles/viewing-contributions-on-your-profile-page)"
