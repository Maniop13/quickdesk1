# quickdesk1
quickdesk ticket intro ,user interface,manging staff etc
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <title>QuickDesk - Simple Help Desk Solution</title>
  
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --primary: #4f46e5;
            --primary-light: #6366f1;
            --primary-dark: #4338ca;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f9fafb;
        }
        
        .animate-pulse {
            animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
        }
        
        @keyframes pulse {
            0%, 100% {
                opacity: 1;
            }
            50% {
                opacity: 0.5;
            }
        }
        
        .ticket-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }
        
        .priority-high {
            border-left: 4px solid #ef4444;
        }
        
        .priority-medium {
            border-left: 4px solid #f59e0b;
        }
        
        .priority-low {
            border-left: 4px solid #10b981;
        }
        
        .status-open {
            background-color: #fef3c7;
            color: #92400e;
        }
        
        .status-in-progress {
            background-color: #dbeafe;
            color: #1e40af;
        }
        
        .status-resolved {
            background-color: #d1fae5;
            color: #065f46;
        }
    </style>
</head>
<body>
    <div class="min-h-screen bg-gray-50">
        <!-- Header -->
        <header class="bg-white shadow-sm">
            <div class="max-w-7xl mx-auto px-4 py-4 sm:px-6 lg:px-8 flex justify-between items-center">
                <div class="flex items-center">
                    <img src="https://placehold.co/40x40" alt="QuickDesk logo - a blue desk calendar with a checkmark" class="h-10 w-10 rounded-md">
                    <h1 class="ml-3 text-xl font-bold text-gray-900">QuickDesk</h1>
                </div>
                <div class="flex items-center space-x-4">
                    <button id="user-menu-button" class="flex items-center text-sm rounded-full focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                        <span class="sr-only">Open user menu</span>
                        <div class="h-8 w-8 rounded-full bg-indigo-100 flex items-center justify-center">
                            <span class="text-indigo-600 font-medium">U</span>
                        </div>
                        <span class="ml-2 text-gray-700">User</span>
                    </button>
                    <button id="logout-btn" class="text-gray-500 hover:text-gray-700">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1" />
                        </svg>
                    </button>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <main class="max-w-7xl mx-auto px-4 py-6 sm:px-6 lg:px-8">
            <div class="flex flex-col lg:flex-row gap-6">
                <!-- Sidebar -->
                <aside class="lg:w-1/4 w-full">
                    <div class="bg-white rounded-lg shadow p-4">
                        <h2 class="text-lg font-medium text-gray-900 mb-4">Navigation</h2>
                        <nav class="space-y-1">
                            <button id="dashboard-tab" class="w-full flex items-center px-3 py-2 text-sm font-medium rounded-md text-white bg-indigo-600 group">
                                <svg class="mr-3 h-5 w-5 text-indigo-300" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />
                                </svg>
                                Dashboard
                            </button>
                            <button id="new-ticket-tab" class="w-full flex items-center px-3 py-2 text-sm font-medium rounded-md text-gray-700 hover:text-indigo-600 hover:bg-indigo-50 group">
                                <svg class="mr-3 h-5 w-5 text-gray-400 group-hover:text-indigo-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6" />
                                </svg>
                                New Ticket
                            </button>
                            <button id="my-tickets-tab" class="w-full flex items-center px-3 py-2 text-sm font-medium rounded-md text-gray-700 hover:text-indigo-600 hover:bg-indigo-50 group">
                                <svg class="mr-3 h-5 w-5 text-gray-400 group-hover:text-indigo-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
                                </svg>
                                My Tickets
                            </button>
                            <button id="all-tickets-tab" class="w-full flex items-center px-3 py-2 text-sm font-medium rounded-md text-gray-700 hover:text-indigo-600 hover:bg-indigo-50 group">
                                <svg class="mr-3 h-5 w-5 text-gray-400 group-hover:text-indigo-600" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10" />
                                </svg>
                                All Tickets (Admin)
                            </button>
                        </nav>
                    </div>
                    
                    <!-- Filters for admin view -->
                    <div id="admin-filters" class="bg-white rounded-lg shadow p-4 mt-4 hidden">
                        <h2 class="text-lg font-medium text-gray-900 mb-4">Filters</h2>
                        <div class="space-y-4">
                            <div>
                                <label for="status-filter" class="block text-sm font-medium text-gray-700">Status</label>
                                <select id="status-filter" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
                                    <option value="all">All</option>
                                    <option value="open">Open</option>
                                    <option value="in-progress">In Progress</option>
                                    <option value="resolved">Resolved</option>
                                </select>
                            </div>
                            <div>
                                <label for="priority-filter" class="block text-sm font-medium text-gray-700">Priority</label>
                                <select id="priority-filter" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm rounded-md">
                                    <option value="all">All</option>
                                    <option value="high">High</option>
                                    <option value="medium">Medium</option>
                                    <option value="low">Low</option>
                                </select>
                            </div>
                            <button id="apply-filters" class="w-full bg-indigo-600 text-white py-2 px-4 rounded-md hover:bg-indigo-700">Apply Filters</button>
                        </div>
                    </div>
                </aside>
                
                <!-- Main Content Area -->
                <div class="lg:w-3/4 w-full">
                    <!-- Dashboard View -->
                    <div id="dashboard-view">
                        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 mb-6">
                            <div class="bg-white rounded-lg shadow p-6">
                                <div class="flex items-center justify-between">
                                    <div>
                                        <p class="text-sm font-medium text-gray-500">Open Tickets</p>
                                        <p class="mt-1 text-3xl font-semibold text-gray-900">12</p>
                                    </div>
                                    <div class="p-3 rounded-full bg-indigo-100 text-indigo-600">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2" />
                                        </svg>
                                    </div>
                                </div>
                            </div>
                            <div class="bg-white rounded-lg shadow p-6">
                                <div class="flex items-center justify-between">
                                    <div>
                                        <p class="text-sm font-medium text-gray-500">In Progress</p>
                                        <p class="mt-1 text-3xl font-semibold text-gray-900">8</p>
                                    </div>
                                    <div class="p-3 rounded-full bg-blue-100 text-blue-600">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
                                        </svg>
                                    </div>
                                </div>
                            </div>
                            <div class="bg-white rounded-lg shadow p-6">
                                <div class="flex items-center justify-between">
                                    <div>
                                        <p class="text-sm font-medium text-gray-500">Resolved Today</p>
                                        <p class="mt-1 text-3xl font-semibold text-gray-900">5</p>
                                    </div>
                                    <div class="p-3 rounded-full bg-green-100 text-green-600">
                                        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                        </svg>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="bg-white rounded-lg shadow overflow-hidden">
                            <div class="px-6 py-4 border-b border-gray-200">
                                <h3 class="text-lg font-medium text-gray-900">Recent Activity</h3>
                            </div>
                            <div class="bg-white overflow-hidden">
                                <ul class="divide-y divide-gray-200">
                                    <li class="px-6 py-4">
                                        <div class="flex items-center">
                                            <div class="min-w-0 flex-1">
                                                <div class="flex items-center">
                                                    <img class="h-10 w-10 rounded-full" src="https://placehold.co/40x40" alt="Profile photo of User A">
                                                    <div class="ml-3">
                                                        <p class="text-sm font-medium text-gray-900">Ticket #1243 was resolved</p>
                                                        <p class="text-sm text-gray-500">by Support Agent • 2 hours ago</p>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </li>
                                    <li class="px-6 py-4">
                                        <div class="flex items-center">
                                            <div class="min-w-0 flex-1">
                                                <div class="flex items-center">
                                                    <img class="h-10 w-10 rounded-full" src="https://placehold.co/40x40" alt="Profile photo of User B">
                                                    <div class="ml-3">
                                                        <p class="text-sm font-medium text-gray-900">Ticket #1242 was assigned to you</p>
                                                        <p class="text-sm text-gray-500">by System • 4 hours ago</p>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </li>
                                    <li class="px-6 py-4">
                                        <div class="flex items-center">
                                            <div class="min-w-0 flex-1">
                                                <div class="flex items-center">
                                                    <img class="h-10 w-10 rounded-full" src="https://placehold.co/40x40" alt="Profile photo of User C">
                                                    <div class="ml-3">
                                                        <p class="text-sm font-medium text-gray-900">Ticket #1241 was created</p>
                                                        <p class="text-sm text-gray-500">by Customer • 6 hours ago</p>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                    
                    <!-- New Ticket Form -->
                    <div id="new-ticket-view" class="hidden">
                        <div class="bg-white shadow overflow-hidden rounded-lg">
                            <div class="px-4 py-5 sm:px-6 border-b border-gray-200">
                                <h3 class="text-lg leading-6 font-medium text-gray-900">Create New Ticket</h3>
                                <p class="mt-1 text-sm text-gray-500">Fill out the form below to submit a new support request.</p>
                            </div>
                            <div class="bg-white px-4 py-5 sm:p-6">
                                <form id="ticket-form">
                                    <div class="grid grid-cols-6 gap-6">
                                        <div class="col-span-6">
                                            <label for="subject" class="block text-sm font-medium text-gray-700">Subject</label>
                                            <input type="text" name="subject" id="subject" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" required>
                                        </div>
                                        
                                        <div class="col-span-6">
                                            <label for="description" class="block text-sm font-medium text-gray-700">Description</label>
                                            <textarea id="description" name="description" rows="4" class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" required></textarea>
                                        </div>
                                        
                                        <div class="col-span-6 sm:col-span-3">
                                            <label for="category" class="block text-sm font-medium text-gray-700">Category</label>
                                            <select id="category" name="category" class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
                                                <option>Technical Issue</option>
                                                <option>Account Problem</option>
                                                <option>Feature Request</option>
                                                <option>Billing Question</option>
                                                <option>Other</option>
                                            </select>
                                        </div>
                                        
                                        <div class="col-span-6 sm:col-span-3">
                                            <label for="priority" class="block text-sm font-medium text-gray-700">Priority</label>
                                            <select id="priority" name="priority" class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm">
                                                <option value="low">Low</option>
                                                <option value="medium" selected>Medium</option>
                                                <option value="high">High</option>
                                            </select>
                                        </div>
                                        
                                        <div class="col-span-6">
                                            <div class="flex items-center">
                                                <input id="file-upload" name="file-upload" type="file" class="hidden">
                                                <label for="file-upload" class="cursor-pointer bg-white py-2 px-3 border border-gray-300 rounded-md shadow-sm text-sm leading-4 font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                                                    <svg class="-ml-1 mr-2 h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                                                        <path fill-rule="evenodd" d="M8 4a3 3 0 00-3 3v4a5 5 0 0010 0V7a1 1 0 112 0v4a7 7 0 11-14 0V7a5 5 0 0110 0v4a3 3 0 11-6 0V7a1 1 0 112 0v4a1 1 0 102 0V7a3 3 0 00-3-3z" clip-rule="evenodd" />
                                                    </svg>
                                                    Upload Attachment
                                                </label>
                                                <span id="file-name" class="ml-2 text-sm text-gray-500">No file selected</span>
                                            </div>
                                        </div>
                                    </div>
                                    
                                    <div class="mt-6 flex justify-end">
                                        <button type="button" id="cancel-ticket" class="bg-white py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                                            Cancel
                                        </button>
                                        <button type="submit" class="ml-3 inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
                                            Submit Ticket
                                        </button>
                                    </div>
                                </form>
                            </div>
                        </div>
                    </div>
                    
                    <!-- My Tickets View -->
                    <div id="my-tickets-view" class="hidden">
                        <div class="bg-white shadow overflow-hidden rounded-lg mb-6">
                            <div class="px-4 py-5 sm:px-6 border-b border-gray-200">
                                <h3 class="text-lg leading-6 font-medium text-gray-900">My Tickets</h3>
                                <p class="mt-1 text-sm text-gray-500">A list of all tickets you've submitted.</p>
                            </div>
                            <div class="bg-white divide-y divide-gray-200">
                                <!-- Tickets will be dynamically added here -->
                                <div class="p-4">
                                    <p class="text-sm text-gray-500" id="no-tickets-user">You haven't submitted any tickets yet.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- All Tickets View (Admin) -->
                    <div id="all-tickets-view" class="hidden">
                        <div class="bg-white shadow overflow-hidden rounded-lg mb-6">
                            <div class="px-4 py-5 sm:px-6 border-b border-gray-200">
                                <h3 class="text-lg leading-6 font-medium text-gray-900">All Tickets</h3>
                                <p class="mt-1 text-sm text-gray-500">Manage and resolve all support tickets.</p>
                            </div>
                            <div class="overflow-x-auto">
                                <table class="min-w-full divide-y divide-gray-200">
                                    <thead class="bg-gray-50">
                                        <tr>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">ID</th>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Subject</th>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Priority</th>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Created</th>
                                            <th scope="col" class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody class="bg-white divide-y divide-gray-200">
                                        <!-- Tickets will be dynamically added here -->
                                        <tr>
                                            <td colspan="6" class="px-6 py-4 text-center text-sm text-gray-500" id="no-tickets-admin">There are currently no tickets to display.</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>

    <!-- Ticket Details Modal -->
    <div id="ticket-modal" class="fixed inset-0 overflow-y-auto hidden z-50">
        <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
            <div class="fixed inset-0 transition-opacity" aria-hidden="true">
                <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
            </div>
            <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
            <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-3xl sm:w-full">
                <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="text-lg leading-6 font-medium text-gray-900" id="ticket-modal-subject">Ticket #</h3>
                            <div class="mt-1 flex items-center space-x-2">
                                <span id="ticket-modal-status" class="px-2 py-1 text-xs font-medium rounded-full status-open">Open</span>
                                <span id="ticket-modal-priority" class="px-2 py-1 text-xs font-medium rounded-full bg-gray-100 text-gray-800">Medium</span>
                            </div>
                        </div>
                        <button id="close-modal" type="button" class="text-gray-400 hover:text-gray-500">
                            <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                            </svg>
                        </button>
                    </div>
                    <div class="mt-4">
                        <div class="grid grid-cols-1 gap-y-6 gap-x-4 sm:grid-cols-6">
                            <div class="sm:col-span-3">
                                <label class="block text-sm font-medium text-gray-700">Submitted by</label>
                                <p class="mt-1 text-sm text-gray-900" id="ticket-modal-user">User Name</p>
                            </div>
                            <div class="sm:col-span-3">
                                <label class="block text-sm font-medium text-gray-700">Category</label>
                                <p class="mt-1 text-sm text-gray-900" id="ticket-modal-category">Technical Issue</p>
                            </div>
                            <div class="sm:col-span-3">
                                <label class="block text-sm font-medium text-gray-700">Created</label>
                                <p class="mt-1 text-sm text-gray-900" id="ticket-modal-created">2023-06-15 14:30</p>
                            </div>
                            <div class="sm:col-span-3">
                                <label class="block text-sm font-medium text-gray-700">Assigned to</label>
                                <p class="mt-1 text-sm text-gray-900" id="ticket-modal-assigned">Unassigned</p>
                            </div>
                            <div class="sm:col-span-6">
                                <label class="block text-sm font-medium text-gray-700">Description</label>
                                <div class="mt-1 text-sm text-gray-900 bg-gray-50 p-3 rounded-md" id="ticket-modal-description">
                                    The ticket description would go here.
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
                    <button type="button" id="resolve-ticket" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-green-600 text-base font-medium text-white hover:bg-green-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 sm:ml-3 sm:w-auto sm:text-sm">
                        Resolve Ticket
                    </button>
                    <button type="button" id="assign-to-me" class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-indigo-600 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:ml-3 sm:w-auto sm:text-sm">
                        Assign to Me
                    </button>
                    <button type="button" id="cancel-modal" class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm">
                        Close
                    </button>
                </div>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM elements
            const dashboardView = document.getElementById('dashboard-view');
            const newTicketView = document.getElementById('new-ticket-view');
            const myTicketsView = document.getElementById('my-tickets-view');
            const allTicketsView = document.getElementById('all-tickets-view');
            const adminFilters = document.getElementById('admin-filters');
            
            // Tab buttons
            const dashboardTab = document.getElementById('dashboard-tab');
            const newTicketTab = document.getElementById('new-ticket-tab');
            const myTicketsTab = document.getElementById('my-tickets-tab');
            const allTicketsTab = document.getElementById('all-tickets-tab');
            
            // Ticket form elements
            const ticketForm = document.getElementById('ticket-form');
            const fileUpload = document.getElementById('file-upload');
            const fileName = document.getElementById('file-name');
            const cancelTicket = document.getElementById('cancel-ticket');
            
            // Modal elements
            const ticketModal = document.getElementById('ticket-modal');
            const closeModal = document.getElementById('close-modal');
            const cancelModal = document.getElementById('cancel-modal');
            const resolveTicketBtn = document.getElementById('resolve-ticket');
            const assignToMeBtn = document.getElementById('assign-to-me');
            
            // Sample tickets data
            let tickets = [
                {
                    id: 1001,
                    subject: "Unable to login to dashboard",
                    description: "I've tried resetting my password but still can't access my account. Getting an error message 'Invalid credentials'.",
                    status: "open",
                    priority: "high",
                    category: "Account Problem",
                    createdBy: "John Doe",
                    createdAt: "2023-06-15 09:30",
                    assignedTo: "",
                    attachment: ""
                },
                {
                    id: 1002,
                    subject: "Feature request: Dark mode",
                    description: "Would be great to have a dark mode option in the settings for night time usage.",
                    status: "open",
                    priority: "low",
                    category: "Feature Request",
                    createdBy: "Jane Smith",
                    createdAt: "2023-06-14 14:15",
                    assignedTo: "",
                    attachment: ""
                },
                {
                    id: 1003,
                    subject: "Invoice discrepancy",
                    description: "My June invoice shows an incorrect amount charged compared to what was quoted.",
                    status: "in-progress",
                    priority: "medium",
                    category: "Billing Question",
                    createdBy: "Robert Johnson",
                    createdAt: "2023-06-12 11:45",
                    assignedTo: "Support Agent",
                    attachment: "invoice_screenshot.png"
                },
                {
                    id: 1004,
                    subject: "Mobile app crashing on launch",
                    description: "The app crashes immediately after the splash screen on my iPhone 13 running iOS 16.5.",
                    status: "resolved",
                    priority: "high",
                    category: "Technical Issue",
                    createdBy: "Sarah Williams",
                    createdAt: "2023-06-10 16:20",
                    assignedTo: "Support Agent",
                    attachment: "crash_log.txt"
                }
            ];
            
            // Current user
            const currentUser = {
                name: "User",
                role: "user" // Change to "admin" to see admin features
            };
            
            // Initialize the application
            function init() {
                setupEventListeners();
                showView('dashboard');
                renderMyTickets();
                renderAllTickets();
            }
            
            // Setup event listeners
            function setupEventListeners() {
                // Tab navigation
                dashboardTab.addEventListener('click', () => showView('dashboard'));
                newTicketTab.addEventListener('click', () => showView('new-ticket'));
                myTicketsTab.addEventListener('click', () => showView('my-tickets'));
                allTicketsTab.addEventListener('click', () => showView('all-tickets'));
                
                // Ticket form
                ticketForm.addEventListener('submit', handleTicketSubmit);
                fileUpload.addEventListener('change', updateFileName);
                cancelTicket.addEventListener('click', () => showView('dashboard'));
                
                // Modal controls
                closeModal.addEventListener('click', closeTicketModal);
                cancelModal.addEventListener('click', closeTicketModal);
                resolveTicketBtn.addEventListener('click', resolveTicket);
                assignToMeBtn.addEventListener('click', assignTicketToMe);
            }
            
            // Show a specific view
            function showView(view) {
                dashboardView.classList.add('hidden');
                newTicketView.classList.add('hidden');
                myTicketsView.classList.add('hidden');
                allTicketsView.classList.add('hidden');
                
                if (view === 'dashboard') {
                    dashboardView.classList.remove('hidden');
                    updateActiveTab(dashboardTab);
                } else if (view === 'new-ticket') {
                    newTicketView.classList.remove('hidden');
                    updateActiveTab(newTicketTab);
                } else if (view === 'my-tickets') {
                    myTicketsView.classList.remove('hidden');
                    updateActiveTab(myTicketsTab);
                    renderMyTickets();
                } else if (view === 'all-tickets') {
                    allTicketsView.classList.remove('hidden');
                    adminFilters.classList.remove('hidden');
                    updateActiveTab(allTicketsTab);
                    renderAllTickets();
                }
            }
            
            // Update active tab styling
            function updateActiveTab(activeTab) {
                [dashboardTab, newTicketTab, myTicketsTab, allTicketsTab].forEach(tab => {
                    tab.classList.remove('text-white', 'bg-indigo-600');
                    tab.classList.add('text-gray-700', 'hover:text-indigo-600', 'hover:bg-indigo-50');
                    
                    const icon = tab.querySelector('svg');
                    if (icon) {
                        icon.classList.remove('text-indigo-300');
                        icon.classList.add('text-gray-400');
                        icon.classList.add('group-hover:text-indigo-600');
                    }
                });
                
                activeTab.classList.add('text-white', 'bg-indigo-600');
                activeTab.classList.remove('text-gray-700', 'hover:text-indigo-600', 'hover:bg-indigo-50');
                
                const activeIcon = activeTab.querySelector('svg');
                if (activeIcon) {
                    activeIcon.classList.add('text-indigo-300');
                    activeIcon.classList.remove('text-gray-400', 'group-hover:text-indigo-600');
                }
                
                // Show/hide admin controls based on role
                adminFilters.classList.add('hidden');
                allTicketsTab.classList.add('hidden');
                if (currentUser.role === 'admin') {
                    allTicketsTab.classList.remove('hidden');
                }
            }
            
            // Update file name display when file is selected
            function updateFileName() {
                if (fileUpload.files.length > 0) {
                    fileName.textContent = fileUpload.files[0].name;
                } else {
                    fileName.textContent = 'No file selected';
                }
            }
            
            // Handle ticket form submission
            function handleTicketSubmit(e) {
                e.preventDefault();
                
                const formData = new FormData(ticketForm);
                const ticket = {
                    id: generateTicketId(),
                    subject: formData.get('subject'),
                    description: formData.get('description'),
                    category: formData.get('category'),
                    priority: formData.get('priority'),
                    status: 'open',
                    createdBy: currentUser.name,
                    createdAt: new Date().toISOString(),
                    assignedTo: '',
                    attachment: fileUpload.files.length > 0 ? fileUpload.files[0].name : ''
                };
                
                tickets.unshift(ticket);
                ticketForm.reset();
                fileName.textContent = 'No file selected';
                
                showView('dashboard');
                renderMyTickets();
                renderAllTickets();
                
                // Show success message
                alert('Ticket submitted successfully!');
            }
            
            // Generate a unique ticket ID
            function generateTicketId() {
                const lastTicket = tickets[0];
                return lastTicket ? lastTicket.id + 1 : 1000;
            }
            
            // Render user's tickets
            function renderMyTickets() {
                // Implementation here...
            }

            // Render all tickets (admin)
            function renderAllTickets() {
                // Implementation here...
            }

            // Modal functions
            function closeTicketModal() {
                ticketModal.classList.add('hidden');
            }
            function resolveTicket() {
                // Implementation here...
            }
            function assignTicketToMe() {
                // Implementation here...
            }

            // Initialize app
            init();
        });
    </script>





    import React from "react";

// This is a placeholder App component for your React frontend.
// All backend/server logic should be moved to a separate Node.js project.
function App() {
  return (
    <div>
      <h1>React App</h1>
      <p>Backend API routes should be implemented in a Node.js/Express server, not in this file.</p>
    </div>
  );
}


export default App;
    
</body>
</html>
