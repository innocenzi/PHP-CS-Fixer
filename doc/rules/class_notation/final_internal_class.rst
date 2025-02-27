=============================
Rule ``final_internal_class``
=============================

Internal classes should be ``final``.

Warning
-------

Using this rule is risky
~~~~~~~~~~~~~~~~~~~~~~~~

Changing classes to ``final`` might cause code execution to break.

Configuration
-------------

``annotation_include``
~~~~~~~~~~~~~~~~~~~~~~

.. warning:: This option is deprecated and will be removed in the next major version. Use ``include`` to configure PHPDoc annotations tags and attributes.

Class level attribute or annotation tags that must be set in order to fix the
class (case insensitive).

Allowed types: ``array``

Default value: ``['@internal']``

``annotation_exclude``
~~~~~~~~~~~~~~~~~~~~~~

.. warning:: This option is deprecated and will be removed in the next major version. Use ``exclude`` to configure PHPDoc annotations tags and attributes.

Class level attribute or annotation tags that must be omitted to fix the class,
even if all of the white list ones are used as well (case insensitive).

Allowed types: ``array``

Default value: ``['@final', '@Entity', '@ORM\\Entity', '@ORM\\Mapping\\Entity', '@Mapping\\Entity', '@Document', '@ODM\\Document']``

``include``
~~~~~~~~~~~

Class level attribute or annotation tags that must be set in order to fix the
class (case insensitive).

Allowed types: ``array``

Default value: ``['internal']``

``exclude``
~~~~~~~~~~~

Class level attribute or annotation tags that must be omitted to fix the class,
even if all of the white list ones are used as well (case insensitive).

Allowed types: ``array``

Default value: ``['final', 'Entity', 'ORM\\Entity', 'ORM\\Mapping\\Entity', 'Mapping\\Entity', 'Document', 'ODM\\Document']``

``consider_absent_docblock_as_internal_class``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Whether classes without any DocBlock should be fixed to final.

Allowed types: ``bool``

Default value: ``false``

Examples
--------

Example #1
~~~~~~~~~~

*Default* configuration.

.. code-block:: diff

   --- Original
   +++ New
    <?php
    /**
     * @internal
     */
   -class Sample
   +final class Sample
    {
    }

Example #2
~~~~~~~~~~

With configuration: ``['include' => ['@Custom'], 'exclude' => ['@not-fix']]``.

.. code-block:: diff

   --- Original
   +++ New
    <?php
    /**
     * @CUSTOM
     */
   -class A{}
   +final class A{}

    /**
     * @CUSTOM
     * @not-fix
     */
    class B{}

Rule sets
---------

The rule is part of the following rule set:

- `@PhpCsFixer:risky <./../../ruleSets/PhpCsFixerRisky.rst>`_

