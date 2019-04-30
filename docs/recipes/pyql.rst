Using PyQL
##########

PyQL_ provides a convenient way of defining GraphQL APIs.

.. _PyQL: https://pyql-lib.readthedocs.io/en/latest/

Installation
============

::

    pipenv install pyql


Usage
=====

You can replace the contents of ``app/schema.py`` with the PyQL equivalent.

.. warning::

    PySQL Schema objects need to be compiled into a graphql-core schema
    object before being passed to ``GraphQLView``.

    Replace this line in ``app/app.py``::

         app = create_graphql_app(schema)

    with this::

         app = create_graphql_app(schema.compile())


File: ``app/schema.py``:

.. code-block:: python

    from typing import List

    from pyql import Schema, Object

    from app.db.query.example import (
        create_note, delete_note, get_note, list_notes, update_note)

    schema = Schema()

    Note = Object('Note', {
        'id': int,
        'title': str,
        'body': str,
    })

    @schema.query.field('listNotes')
    def resolve_list_notes(root, info) -> List[Note]:
        return list_notes()

    @schema.query.field('getNote')
    def resolve_list_notes(root, info, id: int) -> Note:
        return get_note(id)

    CreateNoteResult = Object('CreateNoteResult', {'ok': bool, 'note_id': int})

    @schema.mutation.field('createNote')
    def resolve_create_node(root, info) -> CreateNoteResult:
        note_id = create_note(title, body)
        return CreateNoteResult(ok=True, noteId=note_id)

    # ... etc ...
