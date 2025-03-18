import React, { useState, useEffect } from "react";
import "./App.css"; // Import the CSS file

interface Item {
  id: number;
  name: string;
}

const LOCAL_STORAGE_KEY = "todo_items";

const App: React.FC = () => {
  const [items, setItems] = useState<Item[]>([]);
  const [newItem, setNewItem] = useState("");
  const [editId, setEditId] = useState<number | null>(null);

  useEffect(() => {
    const savedItems = localStorage.getItem(LOCAL_STORAGE_KEY);
    if (savedItems) {
      setItems(JSON.parse(savedItems));
    }
  }, []);

  useEffect(() => {
    localStorage.setItem(LOCAL_STORAGE_KEY, JSON.stringify(items));
  }, [items]);

  const addItem = () => {
    if (newItem.trim()) {
      if (editId !== null) {
        setItems(items.map((item) => (item.id === editId ? { ...item, name: newItem } : item)));
        setEditId(null);
      } else {
        setItems([...items, { id: Date.now(), name: newItem }]);
      }
      setNewItem("");
    }
  };

  const editItem = (id: number) => {
    const itemToEdit = items.find((item) => item.id === id);
    if (itemToEdit) {
      setNewItem(itemToEdit.name);
      setEditId(id);
    }
  };

  const deleteItem = (id: number) => {
    setItems(items.filter((item) => item.id !== id));
  };

  return (
    <div className="container">
      <h2>React + TypeScript Todo App</h2>
      <input
        type="text"
        value={newItem}
        onChange={(e) => setNewItem(e.target.value)}
        placeholder="Enter item"
      />
      <button className="add-btn" onClick={addItem}>
        {editId !== null ? "Update" : "Add"}
      </button>
      <ul>
        {items.map((item) => (
          <li key={item.id}>
            {item.name}
            <div>
              <button className="list-btn edit-btn" onClick={() => editItem(item.id)}>✏️</button>
              <button className="list-btn delete-btn" onClick={() => deleteItem(item.id)}>❌</button>
            </div>
          </li>
        ))}
      </ul>
    </div>
  );
};

export default App;
