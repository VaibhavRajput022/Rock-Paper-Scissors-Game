# Contact Book
Contact Information: Store name, phone number, email, and address for each contact.
Add Contact: Allow users to add new contacts with their details.
View Contact List: Display a list of all saved contacts with names and phone numbers.
Search Contact: Implement a search function to find contacts by name or phone number.
Update Contact: Enable users to update contact details.
Delete Contact: Provide an option to delete a contact.
User Interface: Design a user-friendly interface for easy interaction

contacts = []

def show_menu():
    print("\n📒 Contact Book Menu:")
    print("1. Add Contact")
    print("2. View All Contacts")
    print("3. Search Contact")
    print("4. Update Contact")
    print("5. Delete Contact")
    print("6. Exit")

def add_contact():
    print("\n➕ Add New Contact")
    name = input("Enter name: ").strip()
    phone = input("Enter phone number: ").strip()
    email = input("Enter email: ").strip()
    address = input("Enter address: ").strip()
    contact = {
        'name': name,
        'phone': phone,
        'email': email,
        'address': address
    }
    contacts.append(contact)
    print("✅ Contact added successfully!")

def view_contacts():
    print("\n📋 All Contacts")
    if not contacts:
        print("No contacts found.")
        return
    for idx, contact in enumerate(contacts, start=1):
        print(f"{idx}. {contact['name']} - {contact['phone']}")

def search_contact():
    print("\n🔍 Search Contact")
    keyword = input("Enter name or phone number to search: ").strip().lower()
    found = False
    for contact in contacts:
        if keyword in contact['name'].lower() or keyword in contact['phone']:
            print("\nContact Found:")
            print_contact(contact)
            found = True
            break
    if not found:
        print("❌ Contact not found.")

def update_contact():
    print("\n✏️ Update Contact")
    name = input("Enter the name of the contact to update: ").strip()
    for contact in contacts:
        if contact['name'].lower() == name.lower():
            print("Leave blank to keep current value.")
            new_name = input(f"Name ({contact['name']}): ") or contact['name']
            new_phone = input(f"Phone ({contact['phone']}): ") or contact['phone']
            new_email = input(f"Email ({contact['email']}): ") or contact['email']
            new_address = input(f"Address ({contact['address']}): ") or contact['address']
            contact.update({
                'name': new_name,
                'phone': new_phone,
                'email': new_email,
                'address': new_address
            })
            print("✅ Contact updated successfully.")
            return
    print("❌ Contact not found.")

def delete_contact():
    print("\n🗑️ Delete Contact")
    name = input("Enter the name of the contact to delete: ").strip()
    for contact in contacts:
        if contact['name'].lower() == name.lower():
            contacts.remove(contact)
            print("✅ Contact deleted successfully.")
            return
    print("❌ Contact not found.")

def print_contact(contact):
    print(f"Name: {contact['name']}")
    print(f"Phone: {contact['phone']}")
    print(f"Email: {contact['email']}")
    print(f"Address: {contact['address']}")

def main():
    print("📇 Welcome to Contact Book!")
    while True:
        show_menu()
        choice = input("\nChoose an option (1-6): ").strip()
        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            update_contact()
        elif choice == '5':
            delete_contact()
        elif choice == '6':
            print("👋 Exiting Contact Book. Goodbye!")
            break
        else:
            print("❌ Invalid choice. Please enter a number from 1 to 6.")
main()
